# Product owner Python Libraries Report - December

# Overview of time spent per category

| Category           | Hours spent  |
|--------------------|-----|
| Technical debt     | 28  |
| Community support  | 14  |
| Bugs & Maintenance | 20  |
| Feature development| 76  |


# Highlights of December 

The main focus this month was creating an interface for ink! contracts to the libraries. This feature request from the Python Substrate community is now released and [being tested](https://github.com/polkascan/py-substrate-interface/issues/56). 

Code examples can be found here: https://github.com/polkascan/py-substrate-interface#ink-contract-interfacing

It was a bit of a puzzle to figure out how the type decomposition in the contract metadata was handled and to integrate it with the already existing type registry for the runtime, in the end the answer was introducing namespaces per contract hash. 

I was in fact so charmed by the way the SCALE types were decomposed in the contract metadata, I will be enthusiastically in favor to have this available for the runtime as well (if possible), as this is a bit cumbersome to administrate this manually in the library for every Substrate implementation.

The timing couldn’t be better, as PatractPy (part of [Kusama treasury proposal #61](https://kusama.polkassembly.io/motion/246)) is going to use our library and this will save them a lot of time on figuring out low level stuff like metadata parsing, constructing contracts calls and decoding contract events, this is all already been taken care of. ;)

# Planning Januari

Because Robert was so kind to [give us an holiday gift](https://medium.com/polkadot-network/rococo-v1-a-holiday-gift-to-the-polkadot-community-9d4da8049769), I think it will be a good idea to start to examine the new features Cumulus will bring and prepare the Python lib as much as possible so developers can build Python apps interacting with parachains and experiment with XCMP.

That's it for now, happy holidays on behalf of the Polkascan team!
