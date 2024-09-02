# Security Considerations

### Security Considerations

1. **Code Quality and Verification**
   * The smart contract code is peer-reviewed, rigorously tested, and formally verified to prevent undesired behavior.
2. **On-Chain Event Logging**
   * All deposit, withdrawal, and winner selection events are recorded on-chain to facilitate transparent off-chain accounting.
3. **Emergency Controls**
   * The contract can halt and resume all deposits and withdrawals in the event of a security breach.
4. **Withdrawal Security**
   * Withdrawals are restricted to the original depositor's address. An admin can withdraw all funds only if a critical security issue arises.
5. **Fairness in Prize Draws**
   * To ensure fairness, the winner number is force-published at the end of each contest before any new deposit or withdrawal.
