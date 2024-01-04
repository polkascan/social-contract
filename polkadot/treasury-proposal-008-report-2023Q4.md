# Maintenance & Support Substrate Python API (Oct-Dec 2023)

For the last four years, Polkascan Foundation has been maintaining the Substrate Python API: [py-substrate-interface](https://github.com/polkascan/py-substrate-interface), [py-scale-codec](https://github.com/polkascan/py-scale-codec) and [several Python bindings](https://github.com/orgs/polkascan/repositories?q=&type=all&language=rust&sort=) for cryptographic RUST crates used by Substrate.

The Substrate Python API is a library, with similar features as [Polkadot-JS API](https://wiki.polkadot.network/docs/polkadotjs#polkadot-js-api). With this API, Python developers can build apps that interact with any Polkadot, Kusama or other Substrate based chain. There are [APIs for different programming languages](https://wiki.polkadot.network/docs/build-tools-index#rpc-and-api-tools) and our API library is at the moment the only one available for the Python programming language.

As of writing [297 Github repositories and 23 Python packages](https://github.com/polkascan/py-substrate-interface/network/dependents?package_id=UGFja2FnZS04OTc2NTczNTM%3D) are depending on the Python API.

With this treasury proposal, we are asking retroactive funding for our activities in the period October until December 2023.  

## Overview of activities

* The main activity has been the development of a version 2 of the libraries (both [API](https://github.com/polkascan/py-substrate-interface/tree/az-v2) and [scale-codec](https://github.com/polkascan/py-scale-codec/tree/az-v2)). The rationale of this new major release is that after 4 years of development and maturing of Substrate, a lot of the initial design decisions can be revised and legacy support can be dropped. This will drastically improve performance and readability of the code. Also there will be async support, which is a much requested feature. We expect a first alpha release in march.

* Parallel with this development, some [issues](https://github.com/polkascan/py-substrate-interface/issues/368) with ink! contract versioning have been fixed in [latest v1.7.5 release](https://github.com/polkascan/py-substrate-interface/releases/tag/v1.7.5).

* Also new alpha versions have been released with MetadataV15 support: https://github.com/polkascan/py-scale-codec/releases/tag/v1.3.0a and https://github.com/polkascan/py-substrate-interface/releases/tag/v1.8.0a
* Technical support on [Github](https://github.com/polkascan/py-substrate-interface/discussions) and in [#polkascan:matrix.org](https://matrix.to/#/#polkascan:matrix.org) and [substrate.stackexchange.com](https://substrate.stackexchange.com/questions/tagged/python) channels

## Overview of time spent

|            | Hours spent  |
|--------------------|-----|
| October     | 20  |
| November  | 57  |
| December |  50 |
| **Total**|  **127**  |

## Treasury Spending Proposal

|                                  |                     Amount |
|:-------------------------------- | --------------------------:|
| Total Services (Including VAT)   |           19,208.75 EUR[^1] |
| Total Treasury Spending Proposal |          2,744.11 DOT [^2] |

Polkascan verified benificary account: [13eDnpY969xLyu7NgnV9bVg5s9dcrq1UyQn7wAuDXxtYyKA6](https://explorer.polkascan.io/polkadot/account/13eDnpY969xLyu7NgnV9bVg5s9dcrq1UyQn7wAuDXxtYyKA6)



## Previous activity reports

* [October 2020](https://github.com/polkascan/social-contract/blob/master/polkadot/treasury-proposal-008-report-202010.md)
* [November 2020](https://github.com/polkascan/social-contract/blob/master/polkadot/treasury-proposal-008-report-202011.md)
* [December 2020](https://github.com/polkascan/social-contract/blob/master/polkadot/treasury-proposal-008-report-202012.md)
* [January 2021](https://github.com/polkascan/social-contract/blob/master/polkadot/treasury-proposal-008-report-202101.md)
* [February 2021](https://github.com/polkascan/social-contract/blob/master/polkadot/treasury-proposal-008-report-202102.md)
* [March 2021](https://github.com/polkascan/social-contract/blob/master/polkadot/treasury-proposal-008-report-202103.md)
* [April 2021](https://github.com/polkascan/social-contract/blob/master/polkadot/treasury-proposal-008-report-202104.md)
* [May 2021](https://github.com/polkascan/social-contract/blob/master/polkadot/treasury-proposal-008-report-202105.md)
* [June 2021](https://github.com/polkascan/social-contract/blob/master/polkadot/treasury-proposal-008-report-202106.md)
* [July 2021](https://github.com/polkascan/social-contract/blob/master/polkadot/treasury-proposal-008-report-202107.md)
* [August 2021](https://github.com/polkascan/social-contract/blob/master/polkadot/treasury-proposal-008-report-202108.md)
* [September 2021](https://github.com/polkascan/social-contract/blob/master/polkadot/treasury-proposal-008-report-202109.md)
* [Quarter 4 2021](https://github.com/polkascan/social-contract/blob/master/polkadot/treasury-proposal-008-report-2021Q4.md)
* [Quarter 1 2022](https://github.com/polkascan/social-contract/blob/master/polkadot/treasury-proposal-008-report-2022Q1.md)
* [Quarter 2 2022](https://github.com/polkascan/social-contract/blob/master/polkadot/treasury-proposal-008-report-2022Q2.md)
* [Quarter 3 2022](https://github.com/polkascan/social-contract/blob/master/polkadot/treasury-proposal-008-report-2022Q3.md)
* [Quarter 4 2022](https://github.com/polkascan/social-contract/blob/master/polkadot/treasury-proposal-008-report-2022Q4.md)
* [Quarter 1 2023](https://github.com/polkascan/social-contract/blob/master/polkadot/treasury-proposal-008-report-2023Q1.md)
* [Quarter 2 & 3 2023](https://github.com/polkascan/social-contract/blob/master/polkadot/treasury-proposal-008-report-2023Q2-Q3.md)

## Links and further details

* [The Social Contract Mechanism](https://github.com/polkascan/social-contract/blob/master/README.md)
* [The Social Contract for Maintenance & Support of Python Libraries](https://github.com/polkascan/social-contract/blob/master/polkadot/social-contract-002.md)
* [Business Plan](https://polkascan.org/wp-content/uploads/2022/03/Business-Plan-Polkascan-Foundation-v20220218.1030.pdf)

## About Polkascan

The [Polkascan Foundation](https://polkascan.org) is a not-for-profit infrastructure service provider and maintainer of Polkadot ecosystem open source software, such as the [Polkascan Explorer](https://github.com/polkascan/explorer) and [Substrate Python API](https://github.com/polkascan/py-substrate-interface). 


[^1]: Please refer to our [Business Plan](https://polkascan.org/wp-content/uploads/2022/03/Business-Plan-Polkascan-Foundation-v20220218.1030.pdf) (page 39) for the composition of our hourly rate.

[^2]: The amount of DOT to cover the expenses will be liquidated in advance from our DOT reserves to prevent foreign exchange risk. For this reason, the price snapshot will be taken on the day of the publication of this Treasury Proposal. [Kraken](https://trade.kraken.com/charts/KRAKEN:DOT-EUR) lists the following spot price on January 4th 2023, 12:23 CET: 7.00 EUR/DOT.

