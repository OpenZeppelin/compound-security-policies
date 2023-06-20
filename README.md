# Compound Security Policies

This respository is intended to define the various, roles, responsibilities, and use cases surrounding the usage and function of the Compound Pause Guardian.

## Stakeholders

The following table outlines the various stakeholders and their roles within the Compound Finance ecosystem. Note: the stakeholder groups are not mutually exclusive.

| Group                    | Primary Role Within Compound    |
| ------------------------ | ------------------------------- |
| Protocol Contributors    | Operations and Development      |
| OpenZeppelin             | Security Services               |
| Gauntlet                 | Risk Management                 |
| Multisig Members         | Contract Administrative Actions |
| Community                | Governance                      |

Protocol contributors includes Compound Labs, community members, and other parties invested in the operations and development of Compound.

### Current Community Multisig Members

| Member             | Address                                    |
| ------------------ | ------------------------------------------ |
| Paul L. (Gauntlet) | 0xDD659911EcBD4458db07Ee7cDdeC79bf8F859AbC |
| 0age (OpenSea)     | 0x7e4A8391C728fEd9069B2962699AB416628B19Fa |
| arr00              | 0x2B384212EDc04Ae8bB41738D05BA20E33277bf33 |
| blck               | 0x54A37d93E57c5DA659F508069Cf65A381b61E189 |
| Jared F.           | 0xF515DCb89e67bb5D52b857d11f6C0cC2aD7D0167 |
| TennisBowling      | 0xC3AaE58Ab81663872dd36d73613eb295b167F546 |



## Assets

Each network has a dedicated Gnosis Safe multisig pause guardian that can be used to execute pause functionality or modify configurations to minimize risk.

The multisig configuration can be copied to a new chain using the script ```create-safe-copy.js``` script provided by OpenZeppelin in the defender-multisig-setup/ folder of the [Compound Cross Chain Pause Demo](https://github.com/OpenZeppelin/compound-cross-chain-pause-demo/tree/main/defender-multisig-setup) project.

Threshold: 4/6
Signers: Gauntlet, Protocol Contributors, Community Members

Once a safe has been copied to a new chain, the safe signers will perform a signing ceremony to ensure that all users are able to sign transactions. The transaction should not be executed until all 6 signers have signed the transaction. Ideally, the transaction will execute a restricted function on the Comet contract, however this is not a strict requirement as this can be tested separately later.

### Signing Process

Multisig Owners are expected to sign the transaction within 30 minutes of it being proposed.

 1. One signer creates the transaction and signs it
 2. Two more signers sign the transaction
 3. When prepared to execute, one last signer signs and executes the transaction

Gas fees for executing the transaction can be paid with funds from the operator faucet by executing the transaction through the operator faucet relayer in Defender. For this, the execution strategy for the relayer should be set to 

## Responsibilities

### Risk Management Guidance

**Owner:** Gauntlet

Provide guidance to the Multisig Members on managing risk during a security incident. This includes but is not limited to:
 - Identify market conditions that pose a risk to Compound, such as:
    - Asset price levels
    - COMP distribution
    - Liquidity levels in borrowing and lending pools
 - Advise on interest rates and borrow/supply limits

For all of the above, Gauntlet should also advise on risk mitigation actions, specifically as it relates to implementing pauses on specific actions during potentially risky events.

### Security Best Practices and Alerting

**Owner:** OpenZeppelin

 - Develop, monitor, and review security alerting
    - Perform additional investigation to determine if alerting poses a security risk to the protocol 
 - Provide guidance on security best practices for implementing pause functionality

### Audits

**Owner:** Community, Protocol Contributors, and OpenZeppelin

Protocol Contributors and the community will ensure that all contracts are audited prior to deployoment. OpenZeppelin will typically take the lead in performing audits, however, the community may choose to get additional audits independent of OpenZeppelin.

### Pause

**Owner:** Multisig Members and OpenZeppelin

Signers for the multisig of a particular chain are responsible for initiating pauses on specific functionality in the presence of a security incident.

### Unpause

**Owner:** Community

In v2, once a pause is in place, it can only be unpaused by a community governance proposal by the DAO and therefore is subject to the 7 day governance process.

In v3, the pause guardian multisig can directly unpause without going through a governance proposal.

### Contract Upgrades

**Owner:** Protocol Contributors

Develop and test contract upgrades. In addition, OpenZeppelin will provide guidance on mitigating security issues and perform audits on contract upgrades intended to resolve security concerns.

