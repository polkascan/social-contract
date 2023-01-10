# Delivery Report for the Polkascan Explorer Improvements (Kusama TP 214)

We are pleased to present the delivery report for the improvements made to the [Polkascan Explorer software stack](https://github.com/polkascan/explorer), as outlined in Kusama Treasury Proposal #214. More information about our project can be found in the [social contract](https://github.com/polkascan/social-contract/blob/master/kusama/treasury-proposal-214.md) and on the [Polkassembly](https://kusama.polkassembly.io/treasury/214) post.

To see these improvements in action, we've created a separate domain that uses a recent subset of Polkadot blockchain data. You can find it at https://explorer-dev.polkascan.io/. Because this code is not backwards-compatible with the current production database, we haven't upgraded the official Polkascan Explorer, yet. 

As stated in the proposal, the following features have been successfully implemented:

* Account-specific events
* Event-based balance transfers per account
* Account-specific staking events (including rewards and slashes)
* Account balance history
* Activation dates for runtimes
* Enhanced back end query performance
* New back end performance logging functionality
* Additional filters on list pages (such as date range, block range, runtime version, etc.)
* Tree view of call arguments and event attributes.

We hope that these enhancements will improve the overall functionality and usability of the Polkascan Explorer. Thank you for your support.

Development has progressed in the following basic respositories of the project:

1. PolkADAPT: https://github.com/polkascan/polkadapt
2. Explorer UI: https://github.com/polkascan/explorer-ui
3. Explorer API: https://github.com/polkascan/explorer-api
4. Harvester: https://github.com/polkascan/harvester
5. Explorer Stack: https://github.com/polkascan/explorer

The remainder of this document provides an account of our activities and design decisions per repository.

## 1. Polkascan Explorer


### 1.1. Overview of time spent per category

| Category         | Hours spent |
|:---------------- | -----------:|
| Project overhead |          30 |
| Development      |         296 |
| *Total*          |       *326* |

We've spent more hours than estimated in our proposal (280 hours), albeit still within reasonable margin.

### 1.2. Result

- Account-specific events

    The harvester process contains a new decoding job that examines all events triggered and extracts the events that contains a `T::AccountId` type. Those events are stored indexed by the account in a new table and also show which attribute in the event contains the account.

    The explorer-api ETL procedure has been changed to reflect the changes in the harvester, for the new added CodecEventIndexAccount model. A new query (get_events_for_account) and subscription (subscribe_new_event_for_account) with filters have been added.


    The explorer-ui has been expanded with new functions added to the [Polkascan explorer adapter](https://github.com/polkascan/polkadapt/tree/main/projects/polkascan-explorer). This functionality fetches a list of [account-specific events](https://github.com/polkascan/polkadapt/tree/main/projects/polkascan-explorer/src/lib/web-socket/account-event.functions.ts). Filters can be used to get more specific events. Multiple new features will be able to use these account-specific events.

    Besides being able to filter the event list by account address, we also show a short list of recent events on the account detail page. 

- Event-based balance transfers per account

    Modifications have been made to the account detail page. The balance transfers table is now based on account events, instead of the formerly generated transfer data points.

    The list of all balance transfers has been reimplemented using the new 'events by account' dataset and filtering it by the right pallet and event name. On this page, it's also possible to filter by a specific account.

- Account-specific staking events

    A new tab has been added to the account detail page that shows staking rewards and slashes for the shown account. It uses a filtered list of staking specific account events. This list is limited in size. To view all staking events for this account, there is a button that opens the events page and filters the data query by that account and the Staking pallet.

- Account balance history

    The account detail page contains a new table showing the account's balances at different moments in time. Account-specific events are used to identify balance changes and retrieve block numbers. The block numbers are used to get the system account at the specific block from the live Substrate node. The balances are then calculated and presented.

    A chart containing the account's balances on a timeline has been added. Hovering over the chart's primary line shows popups with balance information.
    
    Polkadapt's Coingecko adapter fetches the historic USD prices of the chain's native token. If available, Coingecko returns a list of prices at each start of a UTC day. In the chart these USD prices are multiplied with the account's total balance. An indicative historic total USD value of the account is shown as a second line in the chart. These USD values are not to be used as an accurate truth, only indicative.
    
    Calculation and display errors were discovered in the balance component. This component is used throughout the explorer. BN.js has been implemented to fix this issue.

- Activation dates for runtimes

    The runtimes list now contains two new columns. Block number and date of runtime activation.

- Enhanced query performance

    All queries are now executed within a window of 500000 blocks back from it's offset (defaults to the last block). This limit puts less strain on the DBMS since the explorer ui doesn't need more range.

    Pagination on the explorer-ui list pages has been modified to match the Polkascan API block level query limiting. These pages no longer use the traditional pagination component. The component has been removed and has been replaced with a 'search more' button. If there are items available within the current block limit then these items will be added to list. When no more items are left within the current block limit, the limit will be modified. If the genesis block is reached no more items are expected to be returned.

- New backend performance logging functionality

    To gain more insight in GraphQL queries that are run, the api can now log all gql queries in csv format. These logs can then be analyzed, in our case to replay all queries using a load test and instrumentation. There are now two extra options to run the explorer-api, one with gql query logging enabled, which stores all GraphQL events. The other needs an external dependecy to run the API using telemetry (using Signoid). The steps required are updated in the explorer-api readme.


- Additional filters on list pages

    We've added several new filter options to the extrinsics, events and transfers pages. You can now search for items within a specific range of dates and/or blocks. Events can be filtered by account address. You can filter by runtime spec version. As there was not a very clear usecase for separate pages of signed (transaction) and unsigned (inherent) extrinsics, These two pages have been removed in favor of a new 'signed' filter on the regular extrinsics page.


- Tree views (call arguments / event attributes)

    The detail pages for an event and extrinsic present a tree view for arguments/attributes. The user has the ability to expand/collapse the tree. By default the entire tree is collapsed.



### 1.3. Design Decisions

- Account-specific events

    An initial design consideration for the harvester to extract and index the accounts present in events attributes was a DB stored procedure, but the process would be too complex to just rely on SQL functions. The alternative was a new ETL job in Python that could be run separate and parallel to the existing jobs like SCALE-decoding. The take-away is being less efficient in processing speed than the stored procedure alternative, but this will be acceptable as this difference is mostly noticeable in the one-time upgrade per running harvester instance. 


    Events can have multiple attributes containing different accounts. These are stored as multiple records in the new EventAccountIndex table; one record per account attribute. It's the combination of event id and account that makes the unique key to each record. This way, querying events for a specific account is much easier. If in the UI the list of events is filtered by an account, we get our data from the EventAccountIndex table instead of the general Event table. To mitigate the need to JOIN tables while querying, we've decided to duplicate some data in both tables. In the harvester this data is copied into both the Event and EventAccountIndex tables.
    
    Not all data is present in the EventAccountIndex table. Additional information is retrieved in the UI by pulling data from a Substrate Node directly.

- Event-based balance transfers per account

    By using events to determine transfers we can tell that all transfers have succeeded. There wouldn't have been an event taking place for a failed transfer. The downside to this approach is that it's not possible to see failed transfers in this list if you want to.

- Account-specific staking events

    As in the balance transfers, all staking related items are based on the events in the Staking pallet. We've decided to create a reusable component for these different versions of the account-specific events list, with different filters as input for the component. In this case, the component is fed with staking related input parameters.

- Account balance history

    The historical balance consists of a table of events that modified the balance and a chart that presents the balance over time. If historic USD prices are available for the chains native token, these prices will be used to calculate the USD value of the token balance at that moment in time. The USD value will be calculated at each balance change and at the start of every (UTC) day.

    The open source javascript library [Highcharts](https://www.highcharts.com/) will be used. It also has an Angular wrapper and is a well maintained project.

    The chart must be observable (rxjs) based. We expect data to be incrementally added. The chart needs to react to these changes.


- Activation dates for runtimes

    The activation date of a runtime is not a property of the dataset returned by getRuntimes(). It's determined by getting the datetime of a block in a separate query.

- Enhanced query performance

    To prevent queries from locking or crashing the Polkascan API we will introduce query block limiting. This creates a subset of data that can be quickly retrieved. This subset must still be able to use pagination. Next to the block limit an offset must be introduced to continue searching items in former blocks.

- New backend performance logging functionality

    The GraphQL framework has been extended to automatically enforce a limit on all generated queries (before executing user filters). It is a moving window and can be controlled by block_limit_offset and block_limit_count GraphQL parameters. This window size can be adjusted with the BLOCK_LIMIT_COUNT setting.

    The logging of GraphQL queries is done asynchronous to disk, to make the impact on the API performance as minimal as possible.

    To further gain insight in API utilization and its performance characteristics, we can now apply instrumentation to the explorer-api. A new telemetry entrypoint is created to run the api using open-telemetry. Signoz was chosen to monitor these metrics. The details on the steps required to run this is added to the explorer-api readme.

- Additional filters on list pages

    Date and block range filters communicate with Polkadapt using a separate argument for the start and the end date or block. This is different from the way Polkadapt interfaces with the explorer API, in that the start and end parameters are converted to one graphql range filter parameter.

- Tree views (call arguments / event attributes)

    There are cases when an event's arguments or an extrinsic's attributes have a large amount of data in multiple sublevels and/or arrays. In most cases a user is not interested in this data. Therefore we have decided to present the data as a tree view that is initially collapsed.

    After testing the Angular Material tree component we found that it could not be used. It turned out to be incompatible with the data. It could also not handle presentation of known attribute types. We've decided to keep the existing attributes components and modify this into a tree view.

