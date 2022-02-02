# Product owner Python Libraries Report - Q4 2021

## Overview of time spent per category

| Category           | Hours spent  |
|--------------------|-----|
| Technical debt     | 56  |
| Community support  | 84  |
| Bugs & Maintenance |  110 |
| Feature development|  132  |
| **Total**|  **382**  |


Report summary of Q4 2021 for maintenance on the [Python library for interfacing with Substrate](https://github.com/polkascan/py-substrate-interface), as part of the [social contract](https://github.com/polkascan/social-contract/blob/library-maintenance/polkadot/social-contract-002.md):

## Activities

* An important addition to the library was the added support for [ECDSA keypairs and Ethereum style Addresses](https://github.com/polkascan/py-substrate-interface/pull/154) (to use with e.g. Moonbeam and Moonriver) 
* New [ink metadata V1 support](https://github.com/polkascan/py-substrate-interface/pull/152), which introduced a new metadata format, utilizing the same `PortableRegistry` format as the runtime itself.
* Added Karura, Moonbeam and Moonriver type registry
* Added [`ChargeAssetTxPayment` extension](https://github.com/polkascan/py-substrate-interface/commit/f552bf0b4352210ca8f2c205b83e736e886609ab) support (used in Statemint/Statemine)
* Improved support for `MetadataV14` and embedded `PortableRegistry`
* Added [signed extensions](https://github.com/polkascan/py-substrate-interface/pull/163) support when creating/decoding extrinsics, until now this was still static, but now works as intented and follows the available extensions in the metadata
* Added `aarch64` and Python 3.10 wheels for RUST bindings (`py-sr25519-bindings`, `py-ed25519-bindings` and `py-bip39-bindings`) and [available on PyPI](https://pypi.org/project/py-sr25519-bindings/#files)
* [Technical support](https://github.com/polkascan/py-substrate-interface/issues?q=) for Python developers


For more details about deliverables see https://github.com/polkascan/py-substrate-interface/releases and https://github.com/polkascan/py-scale-codec/releases

Link to this report with hour breakdown: https://github.com/polkascan/social-contract/blob/master/polkadot/treasury-proposal-008-report-2021Q4.md
