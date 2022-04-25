# Product owner Python Libraries Report - Q1 2022

## Overview of time spent per category

|            | Hours spent  |
|--------------------|-----|
| January     | 5  |
| February  | 82  |
| March |  5 |
| **Total**|  **92**  |


Report summary of Q1 2022 for maintenance on the [Python library for interfacing with Substrate](https://github.com/polkascan/py-substrate-interface), as part of the [social contract](https://github.com/polkascan/social-contract/blob/library-maintenance/polkadot/social-contract-002.md):

## Activities

* Added support for ink metadata V3 [#188](https://github.com/polkascan/py-substrate-interface/issues/188)
* Added type decomposition information for storage functions, this provides more insight how to format the input parameters of the `query()` function. in [#196](https://github.com/polkascan/py-substrate-interface/issues/196)
* Implemented well-known storage keys in `query()` like `Substrate.Code` in [#193](https://github.com/polkascan/py-substrate-interface/issues/193)
* Added support for verification of wrapped messages [#185](https://github.com/polkascan/py-substrate-interface/issues/185)
* Added missing error information for `ExtrinsicReceipt` in `MetadataV14` [#187](https://github.com/polkascan/py-substrate-interface/issues/187)
* Added convenience method retrieve_extrinsic_by_identifier [#184](https://github.com/polkascan/py-substrate-interface/issues/184)
* Added `WrapperKeepOpaque` type
* Also generate extrinsic_hash for unsigned extrinsics [#69](https://github.com/polkascan/py-scale-codec/issues/69)


For more details about deliverables see https://github.com/polkascan/py-substrate-interface/releases and https://github.com/polkascan/py-scale-codec/releases

Link to this report with hour breakdown: https://github.com/polkascan/social-contract/blob/master/polkadot/treasury-proposal-008-report-2022Q1.md
