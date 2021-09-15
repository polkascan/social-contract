# Product owner Python Libraries Report - August 2021

# Overview of time spent per category

| Category           | Hours spent  |
|--------------------|-----|
| Technical debt     | 24  |
| Community support  | 22  |
| Bugs & Maintenance |  90 |
| Feature development|  0  |
| **Total**|  **136**  |


Hi everyone, reporting in for the (belated) August report summary for maintenance on the [Python library for interfacing with Substrate](https://github.com/polkascan/py-substrate-interface), as part of the [social contract](https://github.com/polkascan/social-contract/blob/library-maintenance/polkadot/social-contract-002.md):

Besides the usual type registry upkeep and community support I spent most time (like last month) on integrating the [scale-info](https://github.com/paritytech/scale-info) project. When this is available in Substrate master, the first production version of the libraries will be released. Because this version will not be completely backwards compatible, the current `0.13.x` branch will continue to be updated with type changes for the time being, to provide some more time for developers to upgrade to the latest version.


Link to this report with hour breakdown: https://github.com/polkascan/social-contract/blob/master/polkadot/treasury-proposal-008-report-202108.md
