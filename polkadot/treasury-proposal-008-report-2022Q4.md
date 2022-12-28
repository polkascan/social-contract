# Product owner Python Libraries Report - Q4 2022

Report summary of Q4 2022 for maintenance on the [Python libraries for interfacing with Substrate](https://github.com/orgs/polkascan/repositories?q=py-&type=all&language=&sort=stargazers), as part of the [social contract](https://github.com/polkascan/social-contract/blob/library-maintenance/polkadot/social-contract-002.md):

## Overview of time spent per category

|            | Hours spent  |
|--------------------|-----|
| October     | 36  |
| November  | 73  |
| December |  65 |
| **Total Q4**|  **174**  |

## Activities


* This quarter a lot of effort is put in improving the documentation and providing more runtime-specific usage information. This resulted in restructuring the repos docs and the introduction of [PySubstrate metadata docs](https://polkascan.github.io/py-substrate-metadata-docs/), which is a resource where the metadata is presented of well-known runtimes in the Polkadot and Kusama ecosystem, with Python examples and type composition information. This aims to simplify the usage of for example storage and call functions using Python.
* In order to be able to generate this type composition information, [new functions](https://github.com/polkascan/py-substrate-interface/pull/263) were introduced to the library. This release brings some potential [breaking changes](https://github.com/polkascan/py-substrate-interface/releases/tag/v1.4.0). 
* Support for runtime API calls (and replaced deprecated RPC calls) in [#272](https://github.com/polkascan/py-substrate-interface/pull/272) (see [docs](https://github.com/polkascan/py-substrate-interface#call-runtime-apis))
* Import/export keypairs from/to PolkadotJS style JSON [#261](https://github.com/polkascan/py-substrate-interface/pull/261). This introduced new [`Keypair.create_from_encrypted_json()`](https://polkascan.github.io/py-substrate-interface/#substrateinterface.Keypair.create_from_encrypted_json) and [`keypair.export_to_encrypted_json()`](https://polkascan.github.io/py-substrate-interface/#substrateinterface.Keypair.export_to_encrypted_json) functions.
* Added ink! v4 metadata support [#254](https://github.com/polkascan/py-substrate-interface/pull/254)
* `WeightV2` support [#252](https://github.com/polkascan/py-substrate-interface/issues/252)
* Refactored `get_type_registry()` [#273](https://github.com/polkascan/py-substrate-interface/pull/273)
* [Several](https://github.com/polkascan/py-scale-codec/compare/v1.0.44...v1.1.4) SCALE-codec type changes
* Technical support in [#polkascan:matrix.org](https://matrix.to/#/#polkascan:matrix.org) and [substrate.stackexchange.com](https://substrate.stackexchange.com/questions/tagged/python) channels


For more details about deliverables see https://github.com/polkascan/py-substrate-interface/releases and https://github.com/polkascan/py-scale-codec/releases

## Treasury Spending Proposal


|                                  |                     Amount |
|:-------------------------------- | --------------------------:|
| Total Services (Including VAT)   |           26,317.50 EUR[^1] |
| Total Treasury Spending Proposal |          6,453.531 DOT [^2] |

Polkascan verified benificary account: [13eDnpY969xLyu7NgnV9bVg5s9dcrq1UyQn7wAuDXxtYyKA6](https://explorer-dev.polkascan.io/polkadot/account/13eDnpY969xLyu7NgnV9bVg5s9dcrq1UyQn7wAuDXxtYyKA6)

## About Polkascan Foundation

[Polkascan Foundation](https://polkascan.org/) is a not-for-profit infrastructure service provider and maintainer of open source software, such as [Polkascan Explorer](https://explorer.polkascan.io/), [Python libraries](https://github.com/polkascan/social-contract/blob/master/polkadot/social-contract-002.md), and new and upcoming tools such as [Polkascan Calendar](https://calendar.polkascan.io).

[^1]: Please refer to our [Business Plan](https://polkascan.org/wp-content/uploads/2022/03/Business-Plan-Polkascan-Foundation-v20220218.1030.pdf) (page 39) for the composition of our hourly rate.

[^2]: The amount of DOT to cover the expenses will be liquidated in advance from our DOT reserves to prevent foreign exchange risk. For this reason the price snapshot will be taken on the day of the publication of this Treasury Proposal. [Kraken](https://trade.kraken.com/charts/KRAKEN:DOT-EUR) lists the following spot price on December 28th 2022, 15:08 CET: 4.0780 EUR/DOT.

Link to this report: https://github.com/polkascan/social-contract/blob/master/polkadot/treasury-proposal-008-report-2022Q4.md
