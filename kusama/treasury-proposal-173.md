# Kusama Treasury Proposal #173: Improving functionality of the Polkascan Calendar Application

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


# Delivery Report

This is the delivery report for the improvements to the [Polkascan Calendar](https://calendar.polkascan.io/) as detailed in our Polkassembly post here: https://kusama.polkassembly.io/treasury/173. 

In general, with this round of enhancements, it has become possible for users to select a large number of (para)chains in the Polkadot and Kusama ecosystem. Users can select which type of events are shown on the calendar. We've also updated the user interface to allow for a large number of event items. And with the implementation of a new responsive design, small screen devices will have no problem viewing the calendar.

The remainder of this document provides an account of our activities and design decisions.

## 1. Polkascan Calendar


### 1.1. Overview of time spent per category

| Category               | Hours spent |
|:---------------------- | -----------:|
| Project overhead       |          32 |
| Development            |         168 |
| Testing & Bugfixing    |          40 |
|                        |             |
| Total                  |         240 |


### 1.2. Result

#### 1.2.1 Add/test all chains

Modifications have been made to the [config file](https://github.com/polkascan/calendar-ui/blob/46bfbc1f76c5152e19b7318d5a9e2094362716d4/src/assets/config.example.json) to add the parachains. The application has been modified to connect to each network and retrieve all relevant calendar data. You can set colors and logo's for each network. Logo images can be added to the assets directory or you can use external url's. Please follow the [instructions](https://github.com/polkascan/calendar-ui/blob/46bfbc1f76c5152e19b7318d5a9e2094362716d4/README.md).
Each network has been tested for proper connection and data retrieval, and whether it doesn't create errors that stall the application.

#### 1.2.2 UI Design improvements

The week view has been revised to match the other views. Day and week views had fixed height columns, but these are now relative to the amount of event items per cell; each cell can have a different height. The time indicator has been made relative to the height of a cell, not the entire column.

Event item styling has improved and is implemented consistently on every view.

On smaller screens, the left sidebar is now hidden by default. It can be displayed by pressing the the new menu button in the top left corner. In this mode, the sidebar hovers above the calendar, while on larger screens the sidebar and calendar are placed side by side.

Also, on smaller screens, calendar items show less information on the month and week views. This decreases the amount of vertical space needed on these devices.


#### 1.2.3 Connection toolbox

We've created a [NetworkManager](https://github.com/polkascan/calendar-ui/blob/46bfbc1f76c5152e19b7318d5a9e2094362716d4/src/app/components/network-manager/network-manager.component.ts) component to enable/disable (para)chains, configure connection parameters, and to add your own custom networks that are not part of the pre-configured set of chains. This interface is presented in a dialog. All changes made by the user are persistent (still active after refreshing the page) by storing them in the browser's LocalStorage.

If a chain is disabled, it will be disconnected to limit resource usage. The user can choose from multiple pre-configured connection endpoints (as deployed in the [config.json](https://github.com/polkascan/calendar-ui/blob/46bfbc1f76c5152e19b7318d5a9e2094362716d4/src/assets/config.example.json) file) or enter their own endpoint url for a specific chain.

Note that the enabling/disabling of chains here is different from the showing/hiding of chains in the network filter, discussed below. The network filter does *not* disconnect the chain - connections are kept intact.

#### 1.2.4 Filters

Filters have been added that show/hide event items without loss of data.

Network filter: Show/Hide event items for a particular chain. Which chains can be shown or hidden is determined by the enabled chains in the NetworkManager.

Categories filter: Show/Hide event items per category. Current categories: Staking, Schedule, Democracy, Parachains, Council, Treasury, Society.

Filters remain in place after browser refresh. They have been made persistent through LocalStorage.


### 1.3. Design Decisions

If a network is disabled, the collected data will be removed. We anticipate that the data will be outdated when the network is enabled again.

We haven't created any functionality for specific events that are only found in a particular parachain. For now, we will use the same event items as are shown in the polkadot.js calendar. We didn't have the time to investigate every network's specific event candidates for calendar inclusion.

Even though calendar events can by hidden by filtering by type of event, we still retrieve data for all items of all types. In other words, we get more data than we need. The event items are merely hidden from display. We did this, because we didn't want to add more complexity to the data collection code.

Because this is an open source application that can be installed by everyone for their own specific needs, the config.json file and network logo images are not added to the code repository. These configuration files should be added locally on the deployment machine. The provided example file can serve as a basis.
