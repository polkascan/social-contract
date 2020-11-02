# Product owner Python Libraries Report - October

The first month kicked off with setting up **project kanban boards** [https://github.com/polkascan/py-substrate-interface/projects](https://github.com/polkascan/py-substrate-interface/projects) for each of the four categories defined in the treasury proposal: Technical debt, Community support, Bugs & Maintenance and Feature development. This way it will be transparent how time will be spent and easily keep track of progress. 


# Overview of time spent per category

| Category           | Hours spent  |
|--------------------|-----|
| Technical debt     | 10  |
| Community support  | 46  |
| Bugs & Maintenance | 49  |
| Feature development| 37  |


# Highlights of October 

There have been several **runtime upgrades** on Polkadot and Kusama that needed attention, like implementing new **Bounty types** in the type registries [https://github.com/polkascan/py-substrate-interface/issues/33](https://github.com/polkascan/py-substrate-interface/issues/33) and added support for **MetadataV12**: [https://github.com/polkascan/py-substrate-interface/issues/30](https://github.com/polkascan/py-substrate-interface/issues/30)

Substantial time has been spent on **answering questions** of and providing support to the community, for example to make a specialized **substrate-node-template type registry** so that an instance of Polkascan can be created that’s compatible with [https://github.com/substrate-developer-hub/substrate-node-template](https://github.com/substrate-developer-hub/substrate-node-template)

I gave some priority to finish some features left on the todo list that were requested from the community, like to add **support for mortal extrinsics**[https://github.com/polkascan/py-substrate-interface/issues/24](https://github.com/polkascan/py-substrate-interface/issues/24) and add support for **ED25519 curve keypairs** in our application Substrate-Interface-API [https://github.com/polkascan/substrate-interface-api/issues/1](https://github.com/polkascan/substrate-interface-api/issues/1) and [https://github.com/polkascan/substrate-interface/issues/3](https://github.com/polkascan/substrate-interface/issues/3)

Also questions popped up on how to use the Python libraries for other chains like **Kulupu** [https://github.com/polkascan/py-substrate-interface/issues/27](https://github.com/polkascan/py-substrate-interface/issues/27) or how **fees are determined** [https://github.com/polkascan/substrate-interface-api/issues/2](https://github.com/polkascan/substrate-interface-api/issues/2)

Pending pull requests have been reviewed and integrated like [https://github.com/polkascan/py-substrate-interface/pull/25](https://github.com/polkascan/py-substrate-interface/pull/25) that provided very useful functionality like the possibility to **iterate over storage key/value pairs**.

There have been added a lot of **unit tests** as an ongoing effort in improving the code coverage and **quality of the code**. 

For a **complete review of activities** see the issue tracker on the Polkascan Github and the project Kanban boards:



*   [https://github.com/polkascan/py-substrate-interface/issues](https://github.com/polkascan/py-substrate-interface/issues)
*   [https://github.com/polkascan/substrate-interface-api/issues](https://github.com/polkascan/substrate-interface-api/issues)
*   [https://github.com/polkascan/substrate-interface/issues](https://github.com/polkascan/substrate-interface/issues)
*   [https://github.com/polkascan/py-substrate-interface/projects/4](https://github.com/polkascan/py-substrate-interface/projects/4)
*   [https://github.com/polkascan/py-substrate-interface/projects/3](https://github.com/polkascan/py-substrate-interface/projects/3)
*   [https://github.com/polkascan/py-substrate-interface/projects/2](https://github.com/polkascan/py-substrate-interface/projects/2)
*   [https://github.com/polkascan/py-substrate-interface/projects/1](https://github.com/polkascan/py-substrate-interface/projects/1)


# Planning of november

This month the focus has been mainly on Bugs & Maintenance and Community support, next month I want to focus more on pressing technical debt issues like **insufficient code coverage** by unit tests and **refactoring the metadata decoding** code so it is in line with the rest of the type registry. 

Also this month I’ve already spent some time how to **implement keypairs with hard- and soft derivation paths** (e.g. //Alice/Bob) with the same mnemonic, I expect to finish this in the beginning of November. 

Furthermore I want to test and research why the library at the moment **can’t handle some extrinsics** like [https://github.com/polkascan/py-substrate-interface/issues/29](https://github.com/polkascan/py-substrate-interface/issues/29)
