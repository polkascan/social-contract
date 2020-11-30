# Product owner Python Libraries Report - November


# Overview of time spent per category

| Category           | Hours spent  |
|--------------------|-----|
| Technical debt     | 52  |
| Community support  | 30  |
| Bugs & Maintenance | 34  |
| Feature development| 20  |


# Highlights of November 

* Long overdue, but finally it's possible to generate keypairs with **hard- and soft derivation path support**, without having to rely on Subkey. (E.g. `keypair = Keypair.create_from_uri(mnemonic + '//hard/soft')`)
* Refactored the use of `RuntimeConfiguration` to [fix issues](https://github.com/polkascan/py-substrate-interface/commit/db7341df09d2604fc06b3145ea28b9903d572396) hindering the library **being used in a multi runtime/chain context**. Shout out to Nathan of LocalCoinSwap for addressing this issue.
* **Reimplemented websocket support**, the initial implementation was too inefficient and not persistent due to async challenges. Now connections are persistent, works in a sync context and [on request](https://github.com/polkascan/py-substrate-interface/issues/46) the websocket connection can also be externally managed and passed through.
* **Python 3.6 support**, the library used some asyncio functions that were incompatible with Python < 3.7, the [necessary backwards compatible changes](https://github.com/polkascan/py-substrate-interface/issues/50) were made.
* [Support and research how to use the library for ink!3 contracts](https://github.com/polkascan/py-substrate-interface/issues/56)
* [Fee estimation helper function](https://github.com/polkascan/py-substrate-interface/issues/45)
* Automated builds and unit tests for all RUST bindings
* Remove deprecated Subkey wrapper references from library (all `Keypair` functionality now natively supported or through RUST-bindings)
* Fixed [issue when signing large extrinsics](https://github.com/polkascan/py-substrate-interface/commit/1280c0d89e55b333e6bd9558c49099660a4e692c)
* Several type registry updates for Polkadot, Kusama and Westend


# Planning December

* Implement ink!3 contract interfacing support
* Metadata refactor to a more uniform type registry version
* Improve exception handling and better descriptive exceptions when extrinsics fail
* Increase overall code coverage

