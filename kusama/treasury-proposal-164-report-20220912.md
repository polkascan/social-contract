# Delivery report: Open-sourcing Polkascan block-explorer stack (Treasury proposal #164)

The release of the [open-source Polkascan block-explorer stack](https://github.com/polkascan/explorer/releases/tag/v1.0) is available, as described in [treasury proposal #164](https://kusama.polkassembly.io/treasury/164). Now everyone can reproduce what is available at polkascan.io by running, extending or hosting our open-source explorer.

## Overview of current state

* Up and running in a [few simple steps and requirements](https://github.com/polkascan/explorer#installation)  for a local dev chain or testnet. 
* Stand-alone data harvester process with the possibility to add other ETL extensions besides the current explorer application
* Schedule custom [periodic storage snapshots](https://github.com/polkascan/explorer#storage-cron) like e.g. `System.Account` or`Balances.TotalIssuance`
* [GraphQL interface](https://github.com/polkascan/explorer-api) for the indexed data with subscriptions on data-changes
* Combining on-chain with indexed datasources with [Polkadapt](https://github.com/polkascan/polkadapt) 
* Easy to customize [Angular Material based UI](https://github.com/polkascan/explorer-ui) 

## New delivered features

* Split the current harvester jobs into a generic category and a application specific category and create an extension frame where applications can register their required data transformation processes. 
* Included in this proposal is an harvester ETL extension for the block-explorer, but in the future also for the [calendar](https://github.com/polkascan/calendar-ui) and other applications mentioned in our business plan.
* Create a new repository to be able to run the whole stack in a single Docker compose command, combine the harvester, explorer [API](https://github.com/polkascan/explorer-api) and [GUI](https://github.com/polkascan/explorer-ui). 
* Implement [open-telemetry](https://opentelemetry.io/) instrumentation to get more insight in current performance bottlenecks 
* Address known performance bottlenecks like for example memory usage with current subscription implementation and DB connection pooling 

## Overview of time spent per category

| Category               | Hours  |
|:---------------------- | ---------:|
| New data harvester application       |          200 | 
| Harvester application extension framework            |         50 | 
| Composite repository + Docs             |         16 |
| Open-telemetry implementation             |         40 |
| Performance tuning             |         40 | 
|                        |  |
| **Total**                  |         **346** |

