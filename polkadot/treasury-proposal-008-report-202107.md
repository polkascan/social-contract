# Product owner Python Libraries Report - July 2021

# Overview of time spent per category

| Category           | Hours spent  |
|--------------------|-----|
| Technical debt     | 36  |
| Community support  | 22  |
| Bugs & Maintenance |  104 |
| Feature development|  0  |
| **Total**|  **162**  |


Hi everyone, reporting in for the July report summary for maintenance on the [Python library for interfacing with Substrate](https://github.com/polkascan/py-substrate-interface), as part of the [social contract](https://github.com/polkascan/social-contract/blob/library-maintenance/polkadot/social-contract-002.md):

The main focus last month was, just like the month before, on integrating the [scale-info](https://github.com/paritytech/scale-info) project, which is now making its way into Substrate master. This will be available as the new `MetadataV14`.

The biggest challenge here was how to integrate this new 'embedded type-registry' in the metadata with the legacy manual administrated type-registries that are currently live and ensure a seemless upgrade when the new `MetadataV14` runtime-upgrade is enacted. 

The first alpha-releases of the libraries [py-scalecodec](https://github.com/polkascan/py-scale-codec/releases/tag/v1.0.0a2) and [py-substrate-interface](https://github.com/polkascan/py-substrate-interface/releases/tag/v1.0.0a1) are published, giving Python developers time to make necessary modifications to their apps with the specified upgrade path.

Link to this report with hour breakdown: https://github.com/polkascan/social-contract/blob/master/polkadot/treasury-proposal-008-report-202107.md
