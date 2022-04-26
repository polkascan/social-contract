# Kusama Treasury Proposal #147

Polkassembly: https://kusama.polkassembly.io/treasury/147

Initial development of Polkascan Calendar

Term: 10 March 2022 - 30 April 2022

This is the first Treasury Proposal for the [Polkascan Calendar](https://calendar.polkascan.io), a new product from the [Polkascan Foundation](https://polkascan.org/), that is an integral part of our [Business Plan](https://polkascan.org/wp-content/uploads/2022/03/Business-Plan-Polkascan-Foundation-v20220218.1030.pdf) (page 18) to provide valuable open source tools to the ecosystem. With this proposal we would like to reimburse the time spent on development of the MVP of Polkascan Calendar. Future development work on this product will take place through reimbursements after delivery on a monthly basis.

The [Polkascan Calendar](https://calendar.polkascan.io) is an open source web application that gives an overview of Substrate-based blockchain events in time. You can connect any Polkadot and Kusama relaychain and parachain to this calendar when running your own instance. We have a live version up and running at https://calendar.polkascan.io/.

It differs from existing calendar applications in the ecosystem by:

* showing events from multiple chains simultaneously in one place,
* (upcoming feature) showing historical events, which are harvested, indexed, and provided by a new open source backend service,
* (upcoming feature) tailoring the types of events to your personal needs,
* providing the open source tools to run it yourself.

[Polkascan Foundation](https://polkascan.org/) is a not-for-profit infrastructure service provider and maintainer of open source software, such as [Polkascan Explorer](https://explorer.polkascan.io/), [Python libraries](https://github.com/polkascan/social-contract/blob/master/polkadot/social-contract-002.md), and new and upcoming tools such as [Polkascan Calendar](https://calendar.polkascan.io).

The report that accounts for the development activities can be found below.


We will be available to answer the Kusama council's questions.


## Polkascan Calendar Progress Report 1

Term: 10 March 2022 - 30 April 2022

We've provided more information and installation instructions in the [README](https://github.com/polkascan/calendar-ui/blob/main/README.md) file.

This document contains the first progress report for the application. We've created a first version, a minimum viable product, that shows certain on-chain events for multiple (para-)blockchains in the Polkadot and Kusama ecosystem. You can view the result of our labor via the first public release on https://calendar.polkascan.io.

You can follow our work in our open source code repository at https://github.com/polkascan/calendar-ui. 

This document provides an account of our activities and design decisions. The next milestone and deliverables will focus on more visible and tangible deliverables.


### 1. Calendar UI


#### 1.1. Overview of time spent per category


| Category               | Hours spent |
|:---------------------- | -----------:|
| Project overhead       |          35 |
| Development            |         181 |
|                        |             |
| Total                  |         216 |


#### 1.2. Result

We've set up an initial version of the Calendar. It shows items derived from different chains. Items are presented in a month, week and day view. For now, we only show upcoming events.

Kusama, Polkadot, Moonbeam and Acala are used as the (para)chains presented in the published calendar at https://calendar.polkascan.io, to showcase the possibility of supporting multiple networks and parachains.

Below github issues formed the basis for the current published calendar.

[1: Add RPC Adapters, Create Polkadapt service](https://github.com/polkascan/calendar-ui/issues/1)
We've added [PolkADAPT](https://www.npmjs.com/package/@polkadapt/core) to the project to be able to connect with various data sources. For now, we only connect to Substrate nodes (RPC) to retrieve the data. A service then parses the (derived) data and converts it into calendar events. These are cached in memory, so they can be used throughout the application.

[2: Setup basic month view](https://github.com/polkascan/calendar-ui/issues/2)
The month view displays a grid of days of the selected month. Each row shows a full week, and each column represents the day of the week. We've decided to show all days of the weeks in this month, even if they're from the previous or next month.

[3: Show on-chain derived events on calendar](https://github.com/polkascan/calendar-ui/issues/3)
The loaded calendar events need to be shown on each view type. How they're presented differs from each view type. The events are filtered and grouped per day, sorted by time, and correctly positioned on the page.

[4: Setup basic week view](https://github.com/polkascan/calendar-ui/issues/4)
The week view shows seven days starting on mondays surrounding the selected date. Each day has a timeline where events are shown only by their time stamps.

[5: setup basic day view](https://github.com/polkascan/calendar-ui/issues/5)
The day view shows a table of 24 hours for the selected date. Events are grouped per hour.

[6: Create button to select and navigate to today in current view](https://github.com/polkascan/calendar-ui/issues/6)
While remaining in the same view type, we need to be able to navigate to the current day.


#### 1.3. Design Decisions

As a minimum viable calendar we wanted a month, week and day view type. Each of the view types has a different presentation of calendar items. We're still experimenting to find the best way to present the event data.

Only the upcoming calendar items are available through the Substrate RPC adapter. We only focus on these items for now, until a historical calendar API has been developed.

We haven't focused on mobile friendly responsive design, because we're still experimenting.

According to international standard ISO 8601, Monday is the first day of the week, so we've adapted the interface to conform to this standard.


#### 1.4. Next steps

We would like to build out the different calendar view types, to improve the visualisation of the calendar items.

To better manage which items are relevant to the user, we want to create filtering options, e.g. choice of chain, type of events, etc.

To be able to show events from the past, a specialized data harvester and API will have to be build. Consequently, we need to create a PolkADAPT Calendar API Adapter to connect with this new API.

Become mobile friendly / Responsive design.

In a later stage we would also like to build a browser notification service that emits (specific) events when these are about to take place.



#### 1.5. Treasury Spending Proposal
- Services: 27000.00 EUR (216 hours)(*)
- 21% VAT: 5670.00 EUR
- -------------------- +
- Total Services: 32670.00 EUR
- Total Services: 201.0833 KSM
- -------------------- +
- Total Treasury Spending Proposal: 201.0833 KSM

(*) The [Business Plan](https://polkascan.org/wp-content/uploads/2022/03/Business-Plan-Polkascan-Foundation-v20220218.1030.pdf) outlines the cost structure of Polkascan Foundation activities on page 39.

#### Appendix: Exchange rate EUR/KSM
Price snapshot was taken on the day of the publication of this Treasury Proposal. [CMC](https://coinmarketcap.com/currencies/kusama/historical-data/) lists the following opening prices as data points on 25 April 2022 for the past 30 day period: 

Date	Open (USD/KSM)*
- Apr 25, 2022	USD 159.50
- Apr 24, 2022	USD 162.42
- Apr 23, 2022	USD 164.71
- Apr 22, 2022	USD 168.63
- Apr 21, 2022	USD 180.37
- Apr 20, 2022	USD 176.54
- Apr 19, 2022	USD 167.24
- Apr 18, 2022	USD 169.28
- Apr 17, 2022	USD 174.25
- Apr 16, 2022	USD 166.11
- Apr 15, 2022	USD 161.11
- Apr 14, 2022	USD 160.06
- Apr 13, 2022	USD 153.86
- Apr 12, 2022	USD 152.50
- Apr 11, 2022	USD 170.64
- Apr 10, 2022	USD 178.50
- Apr 09, 2022	USD 172.16
- Apr 08, 2022	USD 181.56
- Apr 07, 2022	USD 173.84
- Apr 06, 2022	USD 179.86
- Apr 05, 2022	USD 188.65
- Apr 04, 2022	USD 201.57
- Apr 03, 2022	USD 201.14
- Apr 02, 2022	USD 189.62
- Apr 01, 2022	USD 188.17
- Mar 31, 2022	USD 188.23
- Mar 30, 2022	USD 184.07
- Mar 29, 2022	USD 168.50
- Mar 28, 2022	USD 174.10
- Mar 27, 2022	USD 164.28

A thirty-day average trading price across exchanges is determined as: 174.049 USD/KSM. [EUR|USD](https://www.exchangerates.org.uk/EUR-USD-25_04_2022-exchange-rate-history.html) conversion rate on 25 April 2022: 1.0713 USD/EUR. This provides the KSM exchange rate of: 162.47 EUR/KSM.
