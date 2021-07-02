# Product owner Python Libraries Report - June 2021

# Overview of time spent per category

| Category           | Hours spent  |
|--------------------|-----|
| Technical debt     | 12  |
| Community support  | 33  |
| Bugs & Maintenance |  96 |
| Feature development|  0  |
| **Total**|  **141**  |


Hi everyone, presenting the June report summary for maintenance on the [Python library for interfacing with Substrate](https://github.com/polkascan/py-substrate-interface), as part of the [social contract](https://github.com/polkascan/social-contract/blob/library-maintenance/polkadot/social-contract-002.md):

### Summary:

Most time is spent this month creating a PoC on how to integrate the [scale-info](https://github.com/paritytech/scale-info) project into our Python library. 

This is a long anticipated development for us, which is making its way into Substrate and I would like to emphasize the importance of this project not only for our library, but for all Substrate interface libraries in the ecosystem, because this will drastically reduce the maintenance burden on manually upkeeping a type registry per Substrate implementation. 

This will create a more sustainable solution on the long run, because it distributes the work of maintaining a type registry for every Substrate implementation out there from a single point (the library maintainers), to the actual Substrate project teams. 

Other activities include:

* Automated builds and releases for our maintained Rust-bindings like [py-sr25519-bindings](https://github.com/polkascan/py-sr25519-bindings) and [py-bip39-bindings](https://pypi.org/project/py-bip39-bindings/), which increased the number of available arch specific Python wheels.
* Possibility of caching block ranges per runtime upgrade, which will reduce the number of needed RPC calls.
* Type registry updates and processed Polkadot/Kusama runtime upgrades


Link to this report with hour breakdown: https://github.com/polkascan/social-contract/blob/master/polkadot/treasury-proposal-008-report-202106.md
