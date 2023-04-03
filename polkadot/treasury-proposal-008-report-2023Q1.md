# Product owner Python Libraries Report - Q1 2023

## Overview of time spent per category

|            | Hours spent  |
|--------------------|-----|
| January     | 39  |
| February  | 78  |
| March |  85 |
| **Total Q1**|  **202**  |


Report summary of Q1 2023 for maintenance on the [Python libraries for interfacing with Substrate](https://github.com/orgs/polkascan/repositories?q=py-&type=all&language=&sort=stargazers), as part of the [social contract](https://github.com/polkascan/social-contract/blob/library-maintenance/polkadot/social-contract-002.md):

## Activities

* Again an overhaul of the [Python libraries documentation](https://polkascan.github.io/py-substrate-interface/), which resulted in an overall more coherent format. Also the [SCALE-codec docs](https://polkascan.github.io/py-scale-codec/) and [runtime usage documentation](https://polkascan.github.io/py-substrate-metadata-docs/) of the library for Polkadot, Kusama and stand-alone Substrate runtimes are in the same format now. 
* Integration of an extension framework. This extension framework is designed to enhance and improve search capabilities on top of existing functionality provided by the Substrate node. It allows for the integration of third-party search indices, which can be easily interchanged with other data sources that provide the same functionality, as long as they adhere to standardized naming conventions in the extension registry. [See documentation for examples](https://polkascan.github.io/py-substrate-interface/usage/extensions/). A Polkascan API extension and Subsquid extension is planned for Q2.  
* Added `query_multi()` [#333](https://github.com/polkascan/py-substrate-interface/pull/333) and `subscribe_storage()` [#328](https://github.com/polkascan/py-substrate-interface/pull/328) functions that can return results for and subscribe to multiple storage keys in a single RPC call 
* Updated compatibility check for available RPC methods in order to play nice with [Chopsticks](https://docs.moonbeam.network/builders/build/substrate-api/chopsticks/). [#331](https://github.com/polkascan/py-substrate-interface/pull/331)
* Added helper function `pending_extrinsics()` [#318](https://github.com/polkascan/py-substrate-interface/pull/318)
* Autodetect `Address` and `ExtrinsicSignature` types [#317](https://github.com/polkascan/py-substrate-interface/pull/317)
* Included well-known `PalletVersion` storage function [#322](https://github.com/polkascan/py-substrate-interface/pull/322)
* Fixed extrinsic encoding issues for some networks with alternative nested nonce- or signature types [#325](https://github.com/polkascan/py-substrate-interface/pull/325)
* Updated Python bindings for`sr25519`, `ed25519-zebra` and `tiny-bip39` RUST crates to latest PyO3 version
* Technical support in [#polkascan:matrix.org](https://matrix.to/#/#polkascan:matrix.org) and [substrate.stackexchange.com](https://substrate.stackexchange.com/questions/tagged/python) channels


For more details about deliverables see https://github.com/polkascan/py-substrate-interface/releases and https://github.com/polkascan/py-scale-codec/releases

## Treasury Spending Proposal


|                                  |                     Amount |
|:-------------------------------- | --------------------------:|
| Total Services (Including VAT)   |           30,552.50 EUR[^1] |
| Total Treasury Spending Proposal |          5,208.94 DOT [^2] |

Polkascan verified benificary account: [13eDnpY969xLyu7NgnV9bVg5s9dcrq1UyQn7wAuDXxtYyKA6](https://explorer-dev.polkascan.io/polkadot/account/13eDnpY969xLyu7NgnV9bVg5s9dcrq1UyQn7wAuDXxtYyKA6)

## About Polkascan Foundation

[Polkascan Foundation](https://polkascan.org/) is a not-for-profit infrastructure service provider and maintainer of open source software, such as the [Polkascan Explorer](https://explorer.polkascan.io/) and Polkadot ecosystem [Python libraries](https://github.com/polkascan/social-contract/blob/master/polkadot/social-contract-002.md).

[^1]: Please refer to our [Business Plan](https://polkascan.org/wp-content/uploads/2022/03/Business-Plan-Polkascan-Foundation-v20220218.1030.pdf) (page 39) for the composition of our hourly rate.

[^2]: The amount of DOT to cover the expenses will be liquidated in advance from our DOT reserves to prevent foreign exchange risk. For this reason the price snapshot will be taken on the day of the publication of this Treasury Proposal. [Kraken](https://trade.kraken.com/charts/KRAKEN:DOT-EUR) lists the following spot price on April 3rd 2023, 10:39 CET: 5.8654 EUR/DOT.

Link to this report: https://github.com/polkascan/social-contract/blob/master/polkadot/treasury-proposal-008-report-2023Q1.md
