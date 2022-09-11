# Kusama Treasury Proposal #147: Improving functionality of the Polkascan Calendar Application

Polkassembly: https://kusama.polkassembly.io/treasury/173

Term: June 2022 - Augustus 2022


This is the second Treasury Proposal for the [Polkascan Calendar](https://calendar.polkascan.io), a new product from the [Polkascan Foundation](https://polkascan.org/), that is an integral part of our [Business Plan](https://polkascan.org/wp-content/uploads/2022/03/Business-Plan-Polkascan-Foundation-v20220218.1030.pdf) (page 18) to provide open source tools to the ecosystem. With this proposal we ask for funding to continue working on this product. The feature that will be developed under this proposal is described below.

The [Polkascan Calendar](https://calendar.polkascan.io) is an [open source](https://github.com/polkascan/calendar-ui) web application that gives an overview of Substrate-based blockchain events in time. You can connect any Polkadot and Kusama relaychain and parachain to this calendar when running your own instance. We have a live version up and running at https://calendar.polkascan.io/.

## Deliverable: Add all relay chains and parachains to the calendar

In the multichain environment of Kusama (and Polkadot) it must be possible to have an combined overview of *every* calendar event for *every*  in one single calendar view. Because of differences between chains, we expect it will require some time to add each chain, test it's data, and adapt the code to match chain specific events.

At the time of writing, there are more than 70 parachains for Kusama and Polkadot combined. Each chain can show multiple events on a single day, so there is a user interface challenge in presenting the vast amount of calendar data. We need to improve the calendar design. Some examples of current design issues:

- We use absolute positioning on the week view. That's alright for a small number of items per day, but we need something that works for a large amount.
- Week view only shows timestamps.
- Day view items are horizontally aligned and flow out of the page when showing lots of events.
- There is no consistent event item style, yet.
- It's not particularly mobile friendly.

Also, some features have to be developed to be able to tune the calendar to the user's need:

- A component that allows the user to show or hide specific relay chains and parachains. The calendar then shows events only for the selected chains.
- A connection management tool, that shows which endpoint connections are successful, which have failed, and option to reconnect using other endpoints.
- An option to add a custom chain (name and url).
- A filtering tool to show or hide items of certain event types.
- Persistent settings, so that users don't have to filter the calendar on every page refresh.

## Overview of time spent and planned

| Category               | Hours |
|:---------------------- | -----:|
| Add/test all chains    |    60 |
| UI design improvements |    60 |
| Connection toolbox     |    60 |
| Filters                |    60 |
|                        |       |
| Hours total            |   240 |

## Breakdown per category

| Add/test all chains              | 60 Hours |
|:-------------------------------- | --------:|
| Add 70+ chains                   |       16 |
| Test data retrieved per chain    |       20 |
| Test shown events per chain      |       24 |

| UI design improvements           | 60 Hours |
|:-------------------------------- | --------:|
| Day view                         |       16 |
| Week view                        |       28 |
| Month view                       |       16 |

| Connection toolbox               | 60 Hours |
|:-------------------------------- | --------:|
| UI Connection Component          |       32 |
| UI Connection Service            |       28 |

| Connection toolbox               | 60 Hours |
|:-------------------------------- | --------:|
| Filter (Base) Components         |       36 |
| Upgrade data retrieval service   |       24 |


## Team & Planning

The team will consist of two front-end developers and an estimate of duration is 6 weeks until delivery.

## Reporting

Polkascan Foundation will report and evaluate after delivery in the Kusama direction channel.

## Treasury Spending Proposal

|                                  |                    Amount |
|:-------------------------------- | -------------------------:|
| Services                         | 30,000 EUR (240 hours[^1]) |
| 21% VAT                          |                  6,300 EUR |
|                                  |                           |
| Total Services                   |                 36,300 EUR |
| Total Treasury Spending Proposal | 685.90 KSM[^2] |

[^1]: Please refer to our [Business Plan](https://polkascan.org/wp-content/uploads/2022/03/Business-Plan-Polkascan-Foundation-v20220218.1030.pdf) (page 39) for the composition of our hourly rate.




[^2]: The amount of KSM to cover the expenses will be liquidated in advance from our KSM reserves to prevent foreign exchange risk. For this reason the price snapshot will be taken on the day of the publication of this Treasury Proposal. [Kraken](https://trade.kraken.com/charts/KRAKEN:KSM-EUR) lists the following spot price on 21 June 2022, 10:30 CET: 52.9232 EUR/KSM.

## About Polkascan Foundation

[Polkascan Foundation](https://polkascan.org/) is a not-for-profit infrastructure service provider and maintainer of open source software, such as [Polkascan Explorer](https://explorer.polkascan.io/), [Python libraries](https://github.com/polkascan/social-contract/blob/master/polkadot/social-contract-002.md), and new and upcoming tools such as [Polkascan Calendar](https://calendar.polkascan.io).
