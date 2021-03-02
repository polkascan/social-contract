# Product owner Python Libraries Report - February

# Overview of time spent per category

| Category           | Hours spent  |
|--------------------|-----|
| Technical debt     | 12  |
| Community support  | 54  |
| Bugs & Maintenance | 50  |
| Feature development|  14  |
| **Total**|  **130**  |

# Highlights of February

* [Implemented](https://github.com/polkascan/py-scale-codec/commit/5ff62f65642acd8aecf7b5598a4544970e0e0150) `Address20`, `Address32` and `Raw` variants of `MultiAddress` and SS58 rendering
* `query_map` function to [iterate over mapped storage functions](https://github.com/polkascan/py-substrate-interface/commit/586f7f921d61493d3f5f489a4f0e0d11beb71b12), the old `iterate_map` function used the unsafe `state_getPairs` RPC call and couldn't be used over public endpoints. `query_map` implements a more Pythonic way to wrap the paginated `state_getKeysPaged` call and return an iterable which transparantly extends the resultset if needed. Also the resultset are rich `ScaleType` objects in stead of primitives, just like the `query` function.
* Implemented [extended SS58 network ids](https://github.com/polkascan/py-substrate-interface/issues/71); this enables network ids of values 48 to 16,383.
* Implemented [missing identity](https://github.com/polkascan/py-substrate-interface/commit/14b3beeb676f03242d4c9aa2b22bee1c59dd4045) hasher in `iterate_map`
* Increased time spent on support questions and issues

# Outlook for March

* As always keeping an eye on the Substrate repos and translate types and functionality into the Python libraries
* More unit tests about XMP functionality in extrinsics and events
* Continue with the CI pipeline for the RUST bindings, but on hold because of other more pressing 
* Refactor some long overdue technical debt on metadata and extrinsic decoding (still todo)

Link to this report with hour breakdown: https://github.com/polkascan/social-contract/blob/master/polkadot/treasury-proposal-008-report-202102.md
