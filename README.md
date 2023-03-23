# Compound Security Policies

This respository is intended to define the various, roles, responsibilities, and use cases surrounding the usage and function of the Compound Pause Guardian.

## Stakeholders

The following table outlines the various stakeholders and their roles within the Compound Finance ecosystem. Note: the stakeholder groups are not mutually exclusive.

| Group            | Primary Role Within Compound    |
| ---------------- | ------------------------------- |
| Compound Labs    | Operations and Development      |
| OpenZeppelin     | Security Services               |
| Gauntlet         | Risk Management                 |
| Multisig Members | Contract Administrative Actions |
| Community        | Governance                      |

## Assets

Each network has a dedicated Gnosis Safe multisig pause guardian that can be used to execute pause functionality or modify configurations to minimize risk.

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

**Owner:** Compound Labs and OpenZeppelin

Compound Labs will ensure that all contracts are audited prior to deployoment. OpenZeppelin will typically take the lead in performing audits, however, Compound Labs or the community may choose to get additional audits independent of OpenZeppelin.

### Pause

**Owner:** Multisig Members and OpenZeppelin

Signers for the multisig of a particular chain are responsible for initiating pauses on specific functionality in the presence of a security incident.

### Unpause

**Owner:** Community

Once a pause is in place, it can only be unpaused by a community governance proposal by the DAO and therefore is subject to the 7 day governance process.

### Contract Upgrades

**Owner:** Compound Labs

Develop and test contract upgrades. In addition, OpenZeppelin will provide guidance on mitigating security issues and perform audits on contract upgrades intended to resolve security concerns.

## Pause Guardian Use Cases

### Stablecoin Depeg

**Condition:** Stablecoin depegs to below 90% of its intended value AND the price of the asset is hardcoded.

**Actions:** 
 1. Pause borrowing. If desired, a pause can be executed by modifying the borrow caps instead of an explicit pause on borrowing.

### Invalid Price Feed

**Condition:** A price feed is either inaccessible or incorrect.

**Action:** 
 1. Pause liquiditations, if necessary

### Arbitrary Contract Bug

**Condition:** There is a wide variance in the type of potential contract bug and which parts of the protocol they affect.

**Actions:** 
 1. Execute a pause for the affected functionality. 
 2. Develop and audit a fixed contract version
 3. Submit a proposal for the upgraded contract, including an unpause in the proposal.
 4. Cancel any pending non-critical proposals