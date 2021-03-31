# Product owner Python Libraries Report - March 2021

# Overview of time spent per category

| Category           | Hours spent  |
|--------------------|-----|
| Technical debt     | 20  |
| Community support  | 36  |
| Bugs & Maintenance | 40  |
| Feature development|  56  |
| **Total**|  **140**  |


Hi everyone, reporting in with the monthly update for the Python libraries and actually this update concludes the initial term of the [social contract](https://github.com/polkascan/social-contract/blob/library-maintenance/polkadot/social-contract-002.md). After investing the time and effort for half a year and with the feedback I received from the Python community I can say it was rewarding and I am quitte satisfied with the result and focus I could give to develop and mature py-substrate-interface.

As the second term of the social contract has been approved by the Polkadot Council, I'll check in as usual again next month!

### Summary:

* Support for subscriptions, like [storage subscriptions](https://github.com/polkascan/py-substrate-interface#storage-subscriptions) or [new heads](https://github.com/polkascan/py-substrate-interface#subscribe-to-new-block-headers). This was a high demanded feature [(1)](https://github.com/polkascan/py-substrate-interface/issues/83) [(2)](https://github.com/polkascan/py-substrate-interface/issues/90).
* [Refactored](https://github.com/polkascan/py-substrate-interface/pull/91/files) websocket message processing so the library is now usable in a multi-threaded environment. There were several issues [(1)](https://github.com/polkascan/py-substrate-interface/issues/89) [(2)](https://github.com/polkascan/py-substrate-interface/issues/82) reported that this wasn't possible
* Implemented [caching decorators](https://github.com/polkascan/py-substrate-interface/commit/427047841eb6b5025eadb6883463bee073ede94b) for frequently used (and deterministic) functions, which reduces the amount of RPC calls.
* Updated [API documentation](https://polkascan.github.io/py-substrate-interface/)
* As always type registry updates and processed runtime upgrades (following https://github.com/paritytech/substrate/discussions/8370 closely)


Link to this report with hour breakdown: https://github.com/polkascan/social-contract/blob/master/polkadot/treasury-proposal-008-report-202103.md
