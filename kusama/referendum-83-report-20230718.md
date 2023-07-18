# Delivery Report: Polkascan Explorer Upgrade and Subsquid Integration (Kusama Referendum #83)

In response to the [Kusama](https://kusama.network/) Treasury Proposal [Referendum #83](https://kusama.polkassembly.io/referenda/83) we aimed to enhance the Polkascan Explorer by integrating [Subsquid](https://www.subsquid.io/) as a data source, facilitating more versatile and resilient access to blockchain data for the users. You may visit the online [development version of the Explorer](https://explorer-dev.polkascan.io/) to view the working result of our effort. Here is a comprehensive delivery report detailing the work completed.


## 1. PolkADAPT

**Total Development Hours Spent: 264**


### 1.1 Advancements in API Utilization

We've made significant strides in unifying the APIs across all adapters, leading to a more seamless and efficient application development process. Now, application developers can retrieve blockchain data using a common API, eliminating the need to understand the specificities of addressing and processing each data source. This enhancement results in a clean, consistent, and coherent interaction with the PolkAdapt system.

Moreover, the introduction of a common result type across all adapters is another remarkable advancement. The unified result type means developers can expect a standard data structure regardless of the source, simplifying data handling and manipulation in application development.


### 1.2 Data Augmentation with PolkADAPT Core

One of the most significant features of our recent upgrade is the dynamic data augmentation functionality in PolkADAPT's [core](https://github.com/polkascan/polkadapt/blob/3b6e0e6/projects/core/src/lib/core.ts) using [RxJs](https://rxjs.dev/) Observables. As new data related to a particular item arrives from multiple data sources, the core system automatically merges this data with the existing results and pushes the augmented data to the application. This feature is a game-changer as it constantly enriches the available data.

Application developers can harness this feature to decide their approach to UI updates. They can choose to wait for data from all sources before initiating an update or progressively enhance the user interface each time new data properties enter the stream. This flexibility provides a robust toolset for developers, allowing them to fine-tune their application's responsiveness according to the needs and expectations of their user base.

- Transitioned from Promise to RxJS Observable, enhancing async handling and stream management.
- Implemented adapter models augmentation, which combines models from multiple adapters.
- Optimized the system by eliminating the need for an isReady status check.
- Merged objects from different adapters that share the same ID via an internal itemRegistry.
- Updated all tests to validate the new changes.


### 1.3 Existing Adapters

#### 1.3.1 Polkascan adapter

- Modified to expose RxJS Observables.
- Developed helper functions that create a subscription or query WebSocket message, broadcasting its response to an Observable.
- Implemented internal pagination/block range handling. The system now continuously searches until the pageSize is met.

#### 1.3.2 Substrate RPC adapter

- Replaced PolkadotJS passthrough with proprietary adapter call paths.
- Migrated to PolkadotJS RxJS version.
- Added models for all retrievable types.
- Developed functions to fetch Blocks, Headers, Accounts, Identity, Balances, Runtime, Runtime Metadata, and Chain Properties.
- The adapter now caches the fetched metadata.
- Upgraded to the latest version of PolkadotJS.

#### 1.3.3 Coingecko adapter

- Altered to expose RxJS Observables.
- Added a coinId in the config, making the adapter no longer reliant on the network name.


### 1.4 New Subsquid adapter

- Developed a new Subsquid Adapter.
- Based on RxJS Observables.
- Converts fetched objects to match Polkascan Explorer data format.
- Combines data from different Squids using Archive and Giant Squid.
- Created subscriptions that retrieve the latest objects. We use polling to get the latest data, but we've made preparations for future stream based subscriptions when they are implemented in Subsquid.
- Developed functions to fetch Blocks, Chain Properties, Events, Account Events, Extrinsics, and Runtimes.
- Currently, the adapter does not support Logs as they are not available in Subsquid.


## 2. Explorer UI

**Total Development Hours Spent: 164**

- Redesigned Block Harvester to manage PolkADAPT Observables.
- The UI now starts broadcasting subscribed observables automatically without waiting for all adapters to be ready.
- The UI can now use Subsquid as the primary data source and is not dependent on the Polkascan Explorer Adapter.
- The Substrate RPC adapter is still a prerequisite, because it provides information that is currently only available from the Substrate node.
- Modified list and detail pages to handle RxJS Observables.
- The Paginated list base component no longer uses adapter pagination info but stores the lowest block number for fetching the next items.
- Tested all list and detail pages using only the Subsquid adapter.
- Currently, Logs are only available with the Polkascan Explorer Adapter.
- Removed filtering on specVersion in adapters, only changes the Pallet and Call/Event name fields in the Extrinsic and Event lists filters.
- Updated runtime services to cache runtime metadata.
- Converted Event attributes and Extrinsic call arguments JSON from Subsquid adapter using runtime metadata types for better presentation of known types (balances, accountIds with identicon, etc.)
- Upgraded to the latest version of Angular and PolkadotJS.


## 3. What's next?

As we've transitioned the PolkADAPT library and the Polkascan Explorer UI to a more efficient system, the stage is set for more data source integrations. Not only because we can't have enough data, but we like to have even more options to get the data.

We invite parachain teams to try out the open source Polkascan Explorer with the Subsquid integration and let us know how we can be of assistance.

Join us in shaping the future of Polkascan Explorer by suggesting the next innovative feature you'd like to see.


## 4. Conclusion

Through this integration and subsequent upgrades, we have successfully established a robust and user-friendly environment for blockchain data exploration and application development. This work not only brings cost savings for (para)chain teams but also facilitates a cleaner application code development process with our improved software package.

We're immensely proud of the progress we've made on the Polkascan Explorer Upgrade and Subsquid Integration, as documented in this delivery report. We have achieved our main objective of integrating multiple data sources in a coherent and efficient manner, providing an enhanced experience for developers and end users.

A big thank you goes out to the Kusama community for supporting our proposal during [referendum #83](https://kusama.polkassembly.io/referenda/83). This project could not have been realized without your trust and positive vote. We feel deeply honored to contribute to this innovative and passionate community, and your support motivates us to continue improving our software and fostering the growth of the Substrate ecosystem.

We're very satisfied with the end result of our work, and we're confident it will bring significant benefits to application developers and (para)chain teams, making their work more efficient and enjoyable.

Now, we invite the developer community to check out the latest commit of our [PolkADAPT](https://github.com/polkascan/polkadapt/tree/3b6e0e6) and [Explorer UI](https://github.com/polkascan/explorer-ui/tree/eb0f8b6) code base on GitHub, delve into the advanced functionalities, and see for yourself how we're handling blockchain data.

As always, we're eager to hear your feedback and we're looking forward to seeing the amazing applications you'll build with these tools!
