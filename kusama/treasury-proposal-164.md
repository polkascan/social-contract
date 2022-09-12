# Kusama Treasury Proposal #164: Open-sourcing Polkascan block-explorer stack

Polkassembly: https://kusama.polkassembly.io/treasury/164

Term: June 2022 - Augustus 2022

This treasury proposal contains the remaining activities to open-source the new Polkascan explorer stack, which is an integral part of our [Business Plan](https://polkascan.org/wp-content/uploads/2022/03/Business-Plan-Polkascan-Foundation-v20220218.1030.pdf) (page 22) to provide a full-stack open-source block explorer for the Dotsama community

As mentioned in our Business plan paragraph "5.4 Milestones" (page 32), one of our deliverables will be the *Substrate Harvester*. The Substrate Harvester is a general-purpose Substrate application that allows for data harvesting, SCALE-decoding, indexing and structured storage of blockchain data from any Substrate-based node. Development has been done in a private repository, as part of the business plan this component will be open-sourced on delivery, converting its license to GPLv3.

There is already significant time spent on the new Substrate harvester, the current functionality is:

* A cascading job architecture with checks and balances to ensure data is complete and correct, with the possibility to re-run one of the jobs without completely restart the harvest process from scratch (e.g. only run the SCALE-decode job when a decoding error is detected )
* Job that retrieves block, extrinsic and storage data from a (public) node endpoint and stores the binary format in the database
* Job that SCALE decodes previous retrieved data using a custom subclass of [py-substrate-interface](https://github.com/polkascan/py-substrate-interface) that can interface with a DBMS in stead of a Substrate node endpoint
* Job that contains the ETL procedures to transform the harvested and decoded data into a structure required by the [Polkascan explorer API](https://github.com/polkascan/explorer-api)
* Possibility to add and queue periodic storage tasks; for a certain range of blocks or specified interval of blocks the decoded storage result will be stored, for example `Balances.TotalIssuance` or `System.Account`. The harvester will process this queue to store the result of all requested storage keys or storage key prefixes.
* Implemented metrics to be monitored when connected to [Prometheus](https://prometheus.io/)


Besides a reimbursement of a portion of the time already spent on the new Substrate Harvester component, the needed remaining activities to be able to run the complete stack as serviced on polkascan.io are:

- Split the current harvester jobs into a generic category and a application specific category and create an extension frame where applications can register their required data transformation processes. 
- Included in this proposal is an harvester ETL extension for the block-explorer, but in the future also for the [calendar](https://github.com/polkascan/calendar-ui) and other applications mentioned in our business plan.
- Create a new repository to be able to run the whole stack in a single Docker compose command, combine the harvester, explorer [API](https://github.com/polkascan/explorer-api) and [GUI](https://github.com/polkascan/explorer-ui). 
- Implement [open-telemetry](https://opentelemetry.io/) instrumentation to get more insight in current performance bottlenecks 
- Address known performance bottlenecks like for example memory usage with current subscription implementation and DB connection pooling 


## Deliverable
An indexed general purpose open-source block-explorer to use for all Substrate based blockchains, with [a GraphQL API]((https://github.com/polkascan/explorer-api)), real-time subscriptions and the [GUI](https://github.com/polkascan/explorer-ui) as serviced on [explorer.polkascan.io](https://explorer.polkascan.io).

## Overview of time spent and planned

| Category               | Hours  | Expenses |
|:---------------------- | -------|----:|
| New data harvester application       |          200 | 25,000 EUR |
| Harvester application extension framework            |         50 | 6,250 EUR |
| Composite repository + Docs             |         16 | 2,000 EUR |
| Open-telemetry implementation             |         40 | 5,000 EUR |
| Performance tuning             |         40 | 5,000 EUR|
|                        |  |
| **Total**                  |         **346** | **43,250 EUR** |


### Breakdown per category

| New data harvester application   | 200 hours |
|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---:|
| Cascading job architecture with checks and balances to ensure data is complete and correct, with the possibility to re-run one of the jobs without completely restart the harvest process from scratch                                   |  32   |
| Job that retrieves block, extrinsic and storage data from a (public) node endpoint and stores the binary format in the database                                                                                              | 24    |
| Job that SCALE decodes previous retrieved data using a custom subclass of [py-substrate-interface](https://github.com/polkascan/py-substrate-interface) that can interface with a DBMS in stead of a Substrate node endpoint |  40   |
| Job that contains the ETL procedures to transform the harvested and decoded data into a structure required by the [Polkascan explorer API](https://github.com/polkascan/explorer-api)                                        |  48   |
| Possibility to add and queue periodic storage tasks; for a certain range of blocks or specified interval of blocks the decoded storage result will be stored, for example `Balances.TotalIssuance` or `System.Account`. The harvester will process this queue to store the result of all requested storage keys or storage key prefixes.     |  48   |
|Implemented metrics to be monitored when connected to [Prometheus](https://prometheus.io/)  | 8 |


| Harvester application extension framework  | 50 hours|
|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---:|
|  Split the current harvester jobs into a generic category and a application specific category                              |  10   |
| Create an harvester extension architecture where new applications can register to transform the data to their requirements                   | 24    |
| Create the harvester extension for [Polkascan explorer API](https://github.com/polkascan/explorer-api) with existing ETL procedures  |  16   |


| Composite repository + Docs  | 16 hours|
|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---:|
|  Create a new repository to be able to run the whole stack in a single Docker compose command, combine the harvester, explorer [API](https://github.com/polkascan/explorer-api) and [GUI](https://github.com/polkascan/explorer-ui).                              |  12   |
| Write documentation how to run the stack with some examples                   | 4    |


| Open-telemetry implementation  | 40 hours |
|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---:|
|  Implement [open-telemetry](https://opentelemetry.io/) instrumentation to get more insight in current performance bottlenecks                              |  40   |


| Performance tuning   | 40 hours |
|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---:|
|  A time-boxed block of time to address current performance issues like for example memory usage with current subscription implementation and DB connection pooling                              |  40   |


## Team & Planning

The team will consist of two Python developers and an estimate of duration is 6 weeks until delivery

## Reporting

Polkascan Foundation will report and evaluate after delivery in the Kusama direction channel.

## Treasury Spending Proposal


|                                  |                     Amount |
|:-------------------------------- | --------------------------:|
| Services                         | 43,250.00 EUR (346 hours a 125 EUR per hour[^1]) |
| 21% VAT                          |               9,082.50 EUR |
|                                  |                            |
| Total Services                   |              52,332.50 EUR |
| Total Treasury Spending Proposal |                1148.3477 KSM [^2] |



## About Polkascan Foundation

[Polkascan Foundation](https://polkascan.org/) is a not-for-profit infrastructure service provider and maintainer of open source software, such as [Polkascan Explorer](https://explorer.polkascan.io/), [Python libraries](https://github.com/polkascan/social-contract/blob/master/polkadot/social-contract-002.md), and new and upcoming tools such as [Polkascan Calendar](https://calendar.polkascan.io).

[^1]: Please refer to our [Business Plan](https://polkascan.org/wp-content/uploads/2022/03/Business-Plan-Polkascan-Foundation-v20220218.1030.pdf) (page 39) for the composition of our hourly rate.

[^2]: The amount of KSM to cover the expenses will be liquidated in advance from our KSM reserves to prevent foreign exchange risk. For this reason the price snapshot will be taken on the day of the publication of this Treasury Proposal. [Kraken](https://trade.kraken.com/charts/KRAKEN:KSM-EUR) lists the following spot price on 13 June 2022, 21:00 CET: 45.572 EUR/KSM.
