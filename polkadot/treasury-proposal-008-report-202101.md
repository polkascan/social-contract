# Product owner Python Libraries Report - January

# Overview of time spent per category

| Category           | Hours spent  |
|--------------------|-----|
| Technical debt     | 11  |
| Community support  | 78  |
| Bugs & Maintenance | 42  |
| Feature development|  8  |

# Highlights of January

* Keeping the Python libaries in lockstep with latest parachain development, added heaps of new types and Rococo support (also deployed on [Polkascan](https://polkascan.io/rococo)) 
* Added `BitVec` SCALE implementation
* [Improved and consistent error handling](https://github.com/polkascan/py-substrate-interface/issues/68)
* [Possibility to ignore SCALE decoding errors](https://github.com/polkascan/py-substrate-interface/issues/66)
* Updated Polkascan open-source version
* Python 3.9 support
* Spent noticeably more time on technical discussions and support, not only about the Python interface and Polkascan but also general Substrate questions, so the adoption is growing. It is rewarding to see the libraries are increasingly being used, for example by LocalCoinSwap, Rotki and PatractLabs.

# Outlook for february

* As always keeping an eye on the Substrate repos and translate types and functionality into the Python libraries
* Improve CI pipeline for our maintained RUST bindings
* Refactor some long overdue technical debt on metadata and extrinsic decoding

Link to this report with hour breakdown: https://github.com/polkascan/social-contract/blob/master/polkadot/treasury-proposal-008-report-202101.md
