# Product owner Python Libraries Report - September 2021

# Overview of time spent per category

| Category           | Hours spent  |
|--------------------|-----|
| Technical debt     | 104  |
| Community support  | 11  |
| Bugs & Maintenance | 20 |
| Feature development|  4  |
| **Total**|  **139**  |



The first year of the [social contract](https://github.com/polkascan/social-contract/blob/library-maintenance/polkadot/social-contract-002.md) was in september officially a wrap and this month has produced the biggest milestone of the Python library of the year, the [version 1.0 release](https://github.com/polkascan/py-substrate-interface/releases/tag/v1.0.0). 

It was an intensive refactor effort for the library and now enables the use of the embedded type registry in the metadata, so no more manual upkeep of types per runtime, which is a huge reduction of maintainance burden for us.

This month we still had to maintain a hybrid situation, where most Substrate implementations didn't upgrade to `MetadataV14` yet.

An interesting number to point out is that since last year our libraries are being used in more than [100 repositories and packages](https://github.com/polkascan/py-scale-codec/network/dependents?dependent_type=PACKAGE). 

Link to this report with hour breakdown: https://github.com/polkascan/social-contract/blob/master/polkadot/treasury-proposal-008-report-202109.md
