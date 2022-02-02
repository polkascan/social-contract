## Social Contract between Polkadot Network and Polkascan Foundation
This Social Contract aims to serve as an agreement between Polkascan Foundation on one hand and the Polkadot Network Community on the other hand. The Social Contract should be viewed as an off-chain coordination mechanism to advance the relation between Polkadot Network Community and Polkascan Foundation in its role of external service provider. The general context of this Social Contract can be found [here](https://github.com/polkascan/social-contract/blob/master/README.md).

## 1. Introduction
Polkascan Foundation is a not-for-profit infrastructure service provider and maintainer of Polkadot Ecosystem Python Libraries. These libraries have been developed over the past 2.5 years and have so far had our Polkascan Block Explorer stack as primary use-case and form its foundational components. The Python libraries are partly funded by Web3 Foundation grants, they have a generalized nature, suitable for adoption by any Python-based project in the broader Polkadot ecosystem. We have had an increasing engagement with the community to provide structural support for new Python-based projects in the ecosystem. Notable projects/teams using the Python libraries are: LocalCoinSwap, Rotki & Patract Labs. Our monthly development updates provide an overview of our activities as part of our current maintenance & support contract.

Polkascan Foundation has been around from day one in the broader Polkadot ecosystem and has been consistently advocating the use of on-chain treasuries as sustainable source of funding for ecosystem infrastructure components. Polkascan Foundation believes that the Polkadot Treasury should be willing to fund maintenance and support of its infrastructure.

## 2. Services
1. Maintain functioning libraries (specified in section 3)
2. Address technical dept and stay on par with ecosystem developments
3. Increase adoption of the libraries by providing community support
4. Best-effort incident & problem management

## 3. Python Ecosystem Libraries
### 3.1. Python Substrate Interface
The Python Substrate Interface library specializes in interfacing with a Substrate node, providing additional convenience methods to deal with SCALE encoding/decoding, metadata parsing, type registry management and versioning of types.
- Repository: https://github.com/polkascan/py-substrate-interface
- Documentation: https://polkascan.github.io/py-substrate-interface/

### 3.2. Python Scale Codec
The Python SCALE Codec library is a lightweight, efficient, binary serialization and deserialization codec.
- Repository: https://github.com/polkascan/py-scale-codec
- Documentation: https://polkascan.github.io/py-scale-codec/

### 3.3. Python BIP39 Bindings
Python Bindings BIP39 is an interface that exposes methods from a RUST crate and makes them accessible to the Python Interpreter using PyO3.
- Repository: https://github.com/polkascan/py-bip39-bindings
- Documentation: https://docs.rs/py-bip39-bindings/0.1.5/bip39/

### 3.4. Python ED25519 Bindings
Python Bindings ED25519 is an interface that exposes methods from a RUST crate and makes them accessible to the Python Interpreter using PyO3.
- Repository: https://github.com/polkascan/py-ed25519-bindings
- Documentation: https://docs.rs/py-ed25519-bindings/0.1.1/ed25519/

### 3.5. Python SR25519 Bindings
Python Bindings SR25519 is an interface that exposes methods from a RUST crate and makes them accessible to the Python Interpreter using PyO3.
- Repository: https://github.com/polkascan/py-sr25519-bindings
- Documentation: https://docs.rs/py-sr25519-bindings/0.1.2/sr25519/

## 4. Roadmap
### 4.1. General activities
- 0.20 FTU (25% of the requested resources) is budgeted for refactoring activities to account for technical debt as a result of the high flux of Substrate over the past 2 years.
- 0.20 FTU (25% of the requested resources) is budgeted for activities that allow the libraries to stay on par with Substrate development.
- 0.20 FTU (25% of the requested resources) is budgeted for community support activities that allows new Python-based projects to adopt the Python libraries.
- 0.20 FTU (25% of the requested resources) is budgeted for feature development as a result of community requests. 

## 5. Budget for Maintenance and Community Support
Polkascan Foundation has budgeted the maintenance of these libraries and provisioning of adequate community support at an estimated sum of EUR 90,000.00 on an annual basis. This should give a sustainable budget that gets Polkascan 0.80 FTU for a Senior Python Developer with substantial knowledge of Substrate.

## 6. Funding request from the Polkadot Treasury
Polkascan Foundation will make periodic funding requests to the Polkadot Treasury:
1. A recurrent six month pre-paid funding for maintenance and support of the Python Libararies, which totals to 45,000.00 EUR.
2. DOT base-price will be determined by taking a 30 day average price from major exchanges.
3. An additional surplus will be taken into account for taxes owed by Polkascan Foundation.

## 6. Treasury Proposals
This section lists the Treasury Proposals that have been submitted to the Polkadot Treasury.
The details of each of the proposals can be found on the referenced pages:
- [Treasury Proposal 8](https://github.com/polkascan/social-contract/blob/master/polkadot/treasury-proposal-008.md): Term: 1 October 2020 - 31 March 2021
- [Treasury Proposal 38](https://github.com/polkascan/social-contract/blob/master/polkadot/treasury-proposal-038.md): Term: 1 April 2021 - 30 September 2021
- [Treasury Proposal 89](https://github.com/polkascan/social-contract/blob/master/polkadot/treasury-proposal-089.md): Term: 1 October 2021 - 31 December 2021

## 7. Similar Proposals
The Centrifuge project has succesfully applied for Polkadot Treasury funding. 
Details of the Centrifuge application can be found [here](https://polkadot.polkassembly.io/post/39).
Polkascan Foundation's treasury funding requests matches the Centrifuge application in size and activity.

## 8. Reporting
Polkascan Foundation reports on its activities on a monthly basis.
Monthly reports that account for maintenance & support contract activities can be found here:
- [October 2020](https://github.com/polkascan/social-contract/blob/master/polkadot/treasury-proposal-008-report-202010.md)
- [November 2020](https://github.com/polkascan/social-contract/blob/master/polkadot/treasury-proposal-008-report-202011.md)
- [December 2020](https://github.com/polkascan/social-contract/blob/master/polkadot/treasury-proposal-008-report-202012.md)
- [January 2021](https://github.com/polkascan/social-contract/blob/master/polkadot/treasury-proposal-008-report-202101.md)
- [February 2021](https://github.com/polkascan/social-contract/blob/master/polkadot/treasury-proposal-008-report-202102.md)
- [March 2021](https://github.com/polkascan/social-contract/blob/master/polkadot/treasury-proposal-008-report-202103.md)
- [April 2021](https://github.com/polkascan/social-contract/blob/master/polkadot/treasury-proposal-008-report-202104.md)
- [May 2021](https://github.com/polkascan/social-contract/blob/master/polkadot/treasury-proposal-008-report-202105.md)
- [June 2021](https://github.com/polkascan/social-contract/blob/master/polkadot/treasury-proposal-008-report-202106.md)
- [July 2021](https://github.com/polkascan/social-contract/blob/master/polkadot/treasury-proposal-008-report-202107.md)
- [August 2021](https://github.com/polkascan/social-contract/blob/master/polkadot/treasury-proposal-008-report-202108.md)

## 9. License
The Polkascan Block Explorer has historically been the primary use-case for the Python libraries. The license for these Libraries is the Apache 2.0 license.  This license will allow for broader adoption of the libraries and should take away most (if not all) friction for community contributions.
