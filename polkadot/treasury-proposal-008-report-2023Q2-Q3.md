# Maintenance & Support Python Libraries (April to September 2023)

For the last three years, Polkascan Foundation has been maintaining the Polkadot related Python libraries, such as [py-substrate-interface](https://github.com/polkascan/py-substrate-interface), [py-scale-codec](https://github.com/polkascan/py-scale-codec) and [several Python bindings](https://github.com/orgs/polkascan/repositories?q=&type=all&language=rust&sort=) for cryptographic RUST crates used by Substrate. With these libraries, Python developers can easily interact with any Polkadot, Kusama or other Substrate based chain.

As of writing [265 Github repositories and 21 Python packages](https://github.com/polkascan/py-substrate-interface/network/dependents?package_id=UGFja2FnZS04OTc2NTczNTM%3D) are depending on our libraries.

With this treasury proposal, we are asking retroactive funding for our activities in the period April until September 2023.  


## Overview of activities
* Implemented new [Polkascan Explorer](https://github.com/polkascan/py-substrate-interface-extension-polkascan) and [Subsquid](https://github.com/polkascan/py-substrate-interface-extension-subsquid) extensions to the py-substrate-interface [extension framework](https://polkascan.github.io/py-substrate-interface/extensions/). These utilize indexes from Polkascan Explorer and Subsquid API endpoints, so data can be queried and filtered that is not directly possible or very inefficient on the Substrate RPC.
* New [runtime interface](https://github.com/polkascan/py-substrate-interface/tree/az-runtime-interface): more intuitive approach to interface with the runtime functionality, this is planned to be available in the next major release.  
* Added [support for ink! v4](https://github.com/polkascan/py-substrate-interface/pull/347)
* Added [SCALE type definitions](https://github.com/polkascan/py-scale-codec/pull/112) for upcoming `MetadataV15` in Substrate. (Full support is still WIP)
* Added [multiple params as key support](https://github.com/polkascan/py-substrate-interface/pull/351) for `query_map()`
* Add support for runtime calls at other blocks than the most recent [#346](https://github.com/polkascan/py-substrate-interface/pull/346)
* Upgrade contract interface to support `WeightV2` [#337](https://github.com/polkascan/py-substrate-interface/pull/337)
* Updated [metadata docs](https://polkascan.github.io/py-substrate-metadata-docs/) for Polkadot & Kusama parachain and stand-alone runtimes
* Technical support on [Github](https://github.com/polkascan/py-substrate-interface/discussions) and in [#polkascan:matrix.org](https://matrix.to/#/#polkascan:matrix.org) and [substrate.stackexchange.com](https://substrate.stackexchange.com/questions/tagged/python) channels

For more details about deliverables see https://github.com/polkascan/py-substrate-interface/releases and https://github.com/polkascan/py-scale-codec/releases

## Overview of time spent

|            | Hours spent  |
|--------------------|-----|
| April     | 29  |
| May  | 36  |
| June |  34 |
| July | 18  |
| August | 24  |
| September |  23 |
| **Total**|  **164**  |

## Treasury Spending Proposal

|                                  |                     Amount |
|:-------------------------------- | --------------------------:|
| Total Services (Including VAT)   |           24,805 EUR[^1] |
| Total Treasury Spending Proposal |          6,444.70 DOT [^2] |

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

The [Polkascan Foundation](https://polkascan.org) is a not-for-profit infrastructure service provider and maintainer of Polkadot ecosystem open source software, such as the [Polkascan Explorer](https://github.com/polkascan/explorer) and Python client libraries. 


[^1]: Please refer to our [Business Plan](https://polkascan.org/wp-content/uploads/2022/03/Business-Plan-Polkascan-Foundation-v20220218.1030.pdf) (page 39) for the composition of our hourly rate.

[^2]: The amount of DOT to cover the expenses will be liquidated in advance from our DOT reserves to prevent foreign exchange risk. For this reason, the price snapshot will be taken on the day of the publication of this Treasury Proposal. [Kraken](https://trade.kraken.com/charts/KRAKEN:DOT-EUR) lists the following spot price on September 29th 2023, 13:07 CET: 3.8489 EUR/DOT.
