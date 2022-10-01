# Product owner Python Libraries Report - Q3 2022

Report summary of Q3 2022 for maintenance on the [Python libraries for interfacing with Substrate](https://github.com/orgs/polkascan/repositories?q=py-&type=all&language=&sort=stargazers), as part of the [social contract](https://github.com/polkascan/social-contract/blob/library-maintenance/polkadot/social-contract-002.md):

## Overview of time spent per category

|            | Hours spent  |
|--------------------|-----|
| July     | 15  |
| August  | 33  |
| September |  43 |
| **Total Q3**|  **91**  |

## Activities

* Created and added [`ed25519-zebra` Python bindings](https://github.com/polkascan/py-ed25519-zebra-bindings) in order to follow Substrate replacing `ed25519-dalek` (which had [security concerns](https://github.com/MystenLabs/ed25519-unsafe-libs)) [#238](https://github.com/polkascan/py-substrate-interface/pull/238)
* Multisig helper functions ([See example]( https://github.com/polkascan/py-substrate-interface#initiate-and-finalize-multisig-extrinsics)) [#245](https://github.com/polkascan/py-substrate-interface/pull/245)
* Added support to show block author for AURA consensus [#249](https://github.com/polkascan/py-substrate-interface/issues/249)
* Refactored transaction fee calculation (using `TransactionFeePaid` event)  [#242](https://github.com/polkascan/py-substrate-interface/pull/242)
* Introduced helper function to construct call params [236](https://github.com/polkascan/py-substrate-interface/issues/236)
* Scalecodec: Updated Crust network type registry [#75](https://github.com/polkascan/py-scale-codec/issues/75)
* Added missing `PortableRegistry` paths for Karura [#77](https://github.com/polkascan/py-scale-codec/issues/77)
* Technical support in [#polkascan:matrix.org](https://matrix.to/#/#polkascan:matrix.org) and substrate.stackexchange.com channels



For more details about deliverables see https://github.com/polkascan/py-substrate-interface/releases and https://github.com/polkascan/py-scale-codec/releases

## Treasury Spending Proposal


|                                  |                     Amount |
|:-------------------------------- | --------------------------:|
| Total Services (Including VAT)   |           13,763.75 EUR[^1] |
| Total Treasury Spending Proposal |          2,140.09 DOT [^2] |

Polkascan verified benificary account: 13eDnpY969xLyu7NgnV9bVg5s9dcrq1UyQn7wAuDXxtYyKA6

## About Polkascan Foundation

[Polkascan Foundation](https://polkascan.org/) is a not-for-profit infrastructure service provider and maintainer of open source software, such as [Polkascan Explorer](https://explorer.polkascan.io/), [Python libraries](https://github.com/polkascan/social-contract/blob/master/polkadot/social-contract-002.md), and new and upcoming tools such as [Polkascan Calendar](https://calendar.polkascan.io).

[^1]: Please refer to our [Business Plan](https://polkascan.org/wp-content/uploads/2022/03/Business-Plan-Polkascan-Foundation-v20220218.1030.pdf) (page 39) for the composition of our hourly rate.

[^2]: The amount of DOT to cover the expenses will be liquidated in advance from our DOT reserves to prevent foreign exchange risk. For this reason the price snapshot will be taken on the day of the publication of this Treasury Proposal. [Kraken](https://trade.kraken.com/charts/KRAKEN:DOT-EUR) lists the following spot price on 1st October 2022, 11:29 CET: 6.4314 EUR/KSM.

Link to this report: https://github.com/polkascan/social-contract/blob/master/polkadot/treasury-proposal-008-report-2022Q3.md
