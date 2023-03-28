# Pause Guardian Use Cases

## Stablecoin Depeg

**Condition:** Stablecoin depegs to below 90% of its intended value AND the price of the asset is hardcoded.

**Actions:** 
 1. Pause borrowing. If desired, a pause can be executed by modifying the borrow caps instead of an explicit pause on borrowing.

## Invalid Price Feed

**Condition:** A price feed is either inaccessible or incorrect.

**Action:** 
 1. Pause liquiditations, if necessary

## Arbitrary Contract Bug

**Condition:** There is a wide variance in the type of potential contract bug and which parts of the protocol they affect.

**Actions:** 
 1. Execute a pause for the affected functionality. 
 2. Develop and audit a fixed contract version
 3. Submit a proposal for the upgraded contract, including an unpause in the proposal.
 4. Cancel any pending non-critical proposals

 Alternatively, if bug was caused by recent upgrade:

 1. Execute a pause for the affected functionality. 
 2. Submit a proposal to roll back the upgrade that caused the bug, include an unpause in the proposal

## Troublesome Upgrade of Underlying Asset

**Condition:** The implementation of an underlying asset within Compound contains a security issue

**Actions:**
 1. Pause the market for the underlying asset
 2. Submit a proposal for a contract upgrade to remediate the vulernability

Alternatively:

 1. Communicate with the team of the underlying asset and work with them to address the issue

## Malicious Governance Proposal Passed

**Condition:** There is a wide variance in the type of potential contract bug and which parts of the protocol they affect.

**Actions:** 

 1. If the proposal introduces an immediate threat to the security of the protocol, pause all affected functionality within the protocol
 2. Submit a proposal to roll back the previous proposal
