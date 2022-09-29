# Polkascan Explorer Improvements

The [Polkascan block explorer](https://explorer.polkascan.io/) is one of multiple software solutions provided to the open source community by the Polkascan Foundation. As part of our efforts to keep improving on the open source block explorer, we propose to enhance it with the following features:

- Show all events for a specific account. We already show all events in the current version of Polkascan, however this time we want to harvest the relationship between these events and accounts they operate on. For this, the back-end needs a new ETL process and harvester logic to collect this data and an extension of the GraphQL service to expose it. The event attribute data will also be provided int the GraphQL query result. For more detailed information on the event, the state at a given block doesn't need to be harvested on the back-end, but can be fetched on the client using the SubstrateRPCAdapter. On the front-end (and thus in the GrapQl service) there will be a filter for the runtime version, pallet, type of event, date range, and block range.
  Creating the ETL process involves some complexity in determining how the JSON data is best collected and interpreted. We are only interested in specific events with certain attributes. Event specifications can be different between runtime versions, so we need to break down metadata for each version.

- Show all balance transfers. This will be made possible with the above addition of indexed historical event data. Filters will be added for amount range, account, block range and date range.

- Show staking rewards and slashes for an account.

- Show balance history of an account, plus USD equivalent for current and historical price. Based on the indexed event data from the Polkascan API, we'll find all events that might have changed the balance. For every event, we'll retrieve the account balance from the state of the corresponding block. The state will be fetched from the Substrate node. This might not be a perfectly accurate picture of the balance history, but it's a pragmatic solution with a pretty granular result.
  To determine which event types are candidates for balance changes, we'll check the metadata to find attributes that specify a token amount. This will also depend on the runtime version.

- Show runtime dates on the runtime page; when did the runtime upgrade?

- Performance improvements in Polkascan search queries. Currently all queries search the entire set of records to match specific criteria. Waiting time can be dramatically reduced by searching in subsequent sets of a fixed amount of blocks. Requests in the front-end will be turned into limited range requests, that can deliver results in fragments. The front-end will be responsible for searching continuously until the paginated result set is fulfilled. The query batches will be processed sequentially. The search results will show a button to search in the next set of blocks, until genesis is reached. 
  Pagination on the back-end will no longer use counts on the database. Consequently, we won't know if there's a next page or not.

- New back-end performance logging functionality to keep track of query behavior, so we can improve the load tests.

- New filters on current list pages: date range, block range, runtime version (influences pallet and call filters), account.

- Show call arguments and event attributes as an expandable tree view. That would be more user friendly than the fully indented view of the data.


## Overview of time planned

| Category                                   | Hours |
|:------------------------------------------ | -----:|
| All events for an account                  |    96 |
| Balance transfers                          |    16 |
| Staking rewards and slashes for an account |    16 |
| Historical balance of an account           |    40 |
| Runtime dates                              |     8 |
| Query performance improvements             |    56 |
| Performance logging                        |     8 |
| Extra filters                              |    24 |
| Tree view of arguments and attributes      |    16 |
|                                            |       |
| Hours total                                |   280 |


## Breakdown per category

| All events for an account                          | 96 Hours |
|:-------------------------------------------------- | --------:|
| Create ETL process (database, backend)             |       32 |
| Make event index subscription                      |        8 |
| GraphQL queries                                    |       16 |
| Extend front-end adapter for client request        |       16 |
| Create UI for events on account page, with filters |       24 |

| Balance transfers | 16 Hours |
|:----------------- | --------:|
| Implement UI      |        8 |
| Update GraphQL    |        8 |

| Staking rewards and slashes for an account            | 16 Hours |
|:----------------------------------------------------- | --------:|
| UI list on the front-end with filters                 |       16 |

| Historical balance of an account              | 40 Hours |
|:--------------------------------------------- | --------:|
| Mechanism to select candidate event types     |        8 |
| Fetch events and balances                     |       16 |
| Create UI for balance history on account page |       16 |

| Runtime dates          | 8 Hours |
|:---------------------- | -------:|
| Extend GraphQL service |       4 |
| Add dates to front-end |       4 |

| Query performance improvements                        | 56 Hours |
|:----------------------------------------------------- | --------:|
| Back-end service hard limits                          |        8 |
| Split front-end queries with UI to continue searching |       32 |
| Modify pagination                                     |       16 |

| Performance logging | 8 Hours |
|:------------------- | -------:|
| Implement logging   |       8 |

| Extra filters                                       | 24 Hours |
|:--------------------------------------------------- | --------:|
| Update front-end filter flow with new UI components |        8 |
| Update back-end for new filters                     |       16 |

| Tree view of arguments and attributes | 16 Hours |
|:------------------------------------- | --------:|
| Implement UI for expandable tree view |       16 |


## Team & Planning

The team will consist of four developers; two devs focused mainly on the front-end and two on the back-end. We estimate a duration of 7 weeks until delivery.

## Reporting

Polkascan Foundation will report and evaluate after delivery in the Kusama direction channel.

## Treasury Spending Proposal

|                            |           Amount |
|:-------------------------- | ----------------:|
| Hours total                |              280 |
| Hourly rate                |         € 151.25 |
| Services                   |       42,350 EUR |
| Treasury Spending Proposal |   ###.## KSM[^1] |

[^1]: The amount of KSM to cover the expenses will be liquidated in advance from our KSM reserves to prevent foreign exchange risk. For this reason the price snapshot will be taken on the day of the publication of this Treasury Proposal. [Kraken](https://trade.kraken.com/charts/KRAKEN:KSM-EUR) lists the following spot price on ## MONTH 2022, ##:## CET: ##.#### EUR/KSM.

## About Polkascan Foundation

[Polkascan Foundation](https://polkascan.org/) is a not-for-profit infrastructure service provider and maintainer of open source software, such as [Polkascan Explorer](https://explorer.polkascan.io/), [Python libraries](https://github.com/polkascan/social-contract/blob/master/polkadot/social-contract-002.md), and new and upcoming tools such as [Polkascan Calendar](https://calendar.polkascan.io).

Polkascan Kusama beneficiary address: DxrsTtxgLN3iEvTX32kpdyEZbggPn9eHYP3miTdELqw4MPj

