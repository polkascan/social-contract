# Adding Subsquid data sources to Polkascan Explorer through a new abstraction layer in Polkadapt (Kusama Referendum 83)

The [Polkascan block explorer](https://explorer.polkascan.io/) is one of multiple software solutions provided to the open source community by the Polkascan Foundation. In this proposal we outline our wish to integrate [Subsquid](https://subsquid.io/) as a data source for the open source block explorer, while adding a new abstraction layer to the Polkadapt communications library to make it easy for application developers to use multiple sources of data coherently and consistently.

To query archived and optimized blockchain data, the services provided by Subsquid are a good fit for the Polkascan Explorer as an alternative to our own back-end [software stack](https://github.com/polkascan/explorer). We've investigated the possibility of using Subsquid's GraphQL endpoints instead of the GraphQL endpoint provided by our [Explorer API](https://github.com/polkascan/explorer-api). The upside to using these is that you won't have to self-host and manage your own node, database, [Harvester](https://github.com/polkascan/harvester), and API — which can be costly. You can just host a simple low cost webserver for the front-end [Explorer UI](https://github.com/polkascan/explorer-ui) and configure it to use the Subsquid API's only.

Or, you don't have to choose between the two. We would like the Explorer to be able to fetch data from both sources at the same time. If one fails or responds more slowly, the other will provide the same data. In the future we can even take it a step further and implement checks that will alert users of data inconsistencies between sources. This mechanism would bring more reliability *and* verifiability to the presented blockchain data.

These efforts will be fundamental in bringing even more sources of blockchain data to the Explorer in the future. The more data we can provide to the end user in a friendly manner, the better.


## Polkadapt improvements

In the current situation, there's a fair bit of data source specific logic used on the application level, in the UI (outside of Polkadapt). The Polkadapt Adapters don't have a common abstraction layer as of yet. For example, getting block information from a substrate node (using SubstrateRPCAdapter) requires different calls than from the Polkascan API (using ExplorerAdapter). The returned values are also very different in structure and type. For Subsquid we would require yet another adapter with it's own specific low level working.

We don't want application developers to have to run and process different calls depending on the data source they're communicating with. The true purpose of Polkadapt is to become the communications center for blockchain data, where data from multiple sources comes together and morphs into one consistent stream. We would like Polkadapt and it's Adapters to do the heavy-lifting for you, so at the application level you don't have to know how each individual adapter works and responds.

To accomplish this, we want to improve the Polkadapt Core and add an abstraction layer to the existing Adapters, so that there will be a consistent API across all adapters, with compatible responses. Not all data sources can provide the same information, so Polkadapt will have to transform and combine responses from multiple sources. Because these responses don't come in at the same time, Polkadapt will have to be modified to provide RxJS Observable based responses. Amended or updated information will enter the Observable stream as each Adapter finishes it's request. Subscriptions at the application level will watch for these changes and update the user interface accordingly.


Polkadapt itself will not dictate which API calls an Adapter should provide. All Adapters will have to agree on a common API and implement their abstraction layers in a compatible way. This will prevent centralization of the API specification and will allow for more organic growth of the API as each Adapter will bring it's own capabilities.

Should a developer really need to use low level calls from an Adapter (e.g. pass-through Polkadot.js calls), we will provide this functionality.

With the above improvements, Polkadapt will be more attactive to be used as the one stop multi-source data provider for any type of application.


## Polkadapt Subsquid Adapter

We want to create a new adapter that uses the Subsquid Graphql API as an adaptation to the Polkascan Explorer API, and if possible as a full alternative. If necessary the adapter will use multiple graphql calls to generate a response that is compatible with the expected output for the Polkascan Explorer.

The usage of Subsquid will make it easier for the Polkascan Explorer to handle different chains as developers are actively creating Subsquid API's for different (para)chains.

Some examples of the API's we intend to use are:

https://squid.subsquid.io/polkadot-explorer/graphql
https://polkadot.explorer.subsquid.io/graphql

These API's provide other calls with different return values than our own Explorer API. We need to do some conversions to match the desired abstracted API and be compatible with the other Adapters. Some abstraction calls might require multiple Subsquid API calls and some might even depend on the results of other calls. A flexible mechanism is required to have one API for multiple data sources.


## Polkadapt Explorer Adapter

The API provided by the Explorer Adapter will need to align with the common abstracted API. For example, we now have one call that returns all events for an account. In the new API definition we would like to have a specific call for staking rewards. For Subsquid this is a separate GraphQL call, but the Explorer API does not have this. Instead, we need to apply proper filters to the Explorer API's GraphQL query that returns all events for an account and match the output to the new definition. 

The Explorer Adapter will have to be adjusted to handle pagination and block level limiting, as determined by a common pagination scheme in the abstraction layer. At the moment this functionality is handled by the Explorer UI but is not compatible with the Subsquid adapter. When all Explorer API specific logic is moved to this adapter, the Explorer UI will only contain code that will work on both the Explorer Adapter and the Subsquid Adapter.


## Explorer refactoring

The Explorer UI has to be refactored to use the new RxJS-based streams and new API (the abstraction layer) from Polkadapt. This means a lot of data source specific logic will be replaced by the new abstracted Polkadapt calls.

Pagination logic will also be abstracted by Polkadapt to make it work across multiple data sources, so this will need to change as well in the UI.


## Overview of time planned

| Category                                                             | Hours |
|:-------------------------------------------------------------------- | -----:|
| Modify Polkadapt to output Observable data streams                   |    52 |
| Abstraction layer (API) definition based on data source capabilities |    36 |
| Implement abstraction layer in SubstrateRPCAdapter                   |    50 |
| Implement abstraction layer in ExplorerAdapter                       |    38 |
| Implement pagination mechanism in ExplorerAdapter                    |    24 |
| Create new SubsquidAdapter                                           |    88 |
| Modify Explorer UI to use new Polkadapt RxJS based abstraction layer |   140 |
|                                                                      |       |
| Hours total                                                          |   428 |


## Breakdown per category


| Modify Polkadapt to output Observable data streams                                | 52 Hours |
|:--------------------------------------------------------------------------------- | --------:|
| Implement RxJS for data stream output                                             |       12 |
| Convert all output items to Observables and update them for every source's output |       20 |
| Replace Proxy-based mechanism for arbitrary call paths with new API registry      |       20 |


| Abstraction layer (API) definition based on data source capabilities | 36 Hours |
|:-------------------------------------------------------------------- | --------:|
| Register calls and return types                                      |       16 |
| Define metadata for data merging functionality                       |       20 |


| Implement abstraction layer in SubstrateRPCAdapter              | 50 Hours |
|:--------------------------------------------------------------- | --------:|
| Define models                                                   |       10 |
| Modify polkadotjs (pass-through) proxy to use observables       |        8 |
| Add call functions for models (handle polkadotjs subscriptions) |       32 |


| Implement abstraction layer in ExplorerAdapter | 38 Hours |
|:---------------------------------------------- | --------:|
| Define models                                  |       10 |
| Modify current call functions to match models  |       12 |
| Add call functions for unimplemented models    |       16 |


| Implement pagination mechanism in ExplorerAdapter               | 24 Hours |
|:--------------------------------------------------------------- | --------:|
| Implement pagination mechanism to match abstraction requirement |       24 |


| Create new SubsquidAdapter                                                    | 88 Hours |
|:----------------------------------------------------------------------------- | --------:|
| Define models                                                                 |        8 |
| Simulate subscriptions on new blocks, events, etc. through polling mechanisms |       24 |
| Implement pagination mechanism to match abstraction requirement               |       24 |
| Create calls with return types consistent with abstract API                   |       32 |


| Modify Explorer UI to use new Polkadapt RxJS based abstraction layer        | 140 Hours |
|:--------------------------------------------------------------------------- | ---------:|
| Replace Adapter specific data processing with new abstracted API calls      |        40 |
| Make all data items dynamic by nature through Subscriptions                 |        40 |
| Modify BlockHarvester to no longer use different data routes                |        20 |
| Modify UI to show or hide elements based on registered Adapter capabilities |        24 |
| Use new pagination mechanism in adapters to match abstraction requirement   |        16 |




## Team & Planning

The team will consist of two part-time developers. We estimate a duration of 13 weeks of development work.


## Reporting

Polkascan Foundation will report and evaluate after delivery in the Kusama direction channel.


## Treasury Spending Proposal

|                            |           Amount |
|:-------------------------- | ----------------:|
| Hours total                |              428 |
| Hourly rate                |     € 151.25[^1] |
| Services                   |       64,735 EUR |
| Treasury Spending Proposal |     2039 KSM[^2] |

1. Hourly rate consists of our contractors' hourly rate of € 121.00 (including VAT) plus 25% overhead (housing and facilities, accounting, etc.) as specified in our [business plan](https://polkascan.org/wp-content/uploads/2022/03/Business-Plan-Polkascan-Foundation-v20220218.1030.pdf), page 39.

2. The amount of KSM to cover the expenses will be liquidated in advance from our KSM reserves to prevent foreign exchange risk. For this reason the price snapshot will be taken on the day of the publication of this Treasury Proposal. [Kraken](https://trade.kraken.com/charts/KRAKEN:KSM-EUR) lists the following spot price on 30 January 2023, 14:23 CET: 31.75 EUR/KSM.


## About Polkascan Foundation

[Polkascan Foundation](https://polkascan.org/) is a not-for-profit infrastructure service provider and maintainer of open source software, such as [Polkascan Explorer](https://explorer.polkascan.io/), [Python libraries](https://github.com/polkascan/social-contract/blob/master/polkadot/social-contract-002.md), and new and upcoming tools such as [Polkascan Calendar](https://calendar.polkascan.io).

Polkascan Kusama beneficiary address: DxrsTtxgLN3iEvTX32kpdyEZbggPn9eHYP3miTdELqw4MPj
