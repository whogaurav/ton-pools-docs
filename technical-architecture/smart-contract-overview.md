# Smart Contract Overview

TON Pools utilizes both on-chain and off-chain mechanics to manage deposits, staking, prize distributions, and other key functionalities.

#### Core Functionalities

1.  **Managing Deposits and Withdrawals**

    * The contract keeps a record of all deposits.
    * Users can deposit or withdraw TON anytime.
    * Yield generation starts immediately upon deposit.
    * All deposit and withdrawal actions are logged as transaction events.


2. **Staking Deposits to Generate Yield**
   * Currently handled separately from the core contract.
   * Deposits remain in the contract; yield is not generated externally.
   * A 3% yield is distributed on deposits.
   *   **Future Plans**:

       * Integrate staking directly within the core contract.
       * Automate staking and unstaking processes on deposits and withdrawals.


3. **Contest Management**
   * **Weekly Contests**: Start and end times are managed on-chain; contests end every Monday at midnight, and a new contest starts immediately after.
   * **Future Plans**:
     * Introduce contests with varying frequencies (daily, monthly, annually).
     * Enable multiple winners per contest.
   *   **Accounting of Winnings**:

       * Tracks total deposits over time using `totalPerSecUserDeposit` (the product of TON deposits held and the time held).
       * This value is updated with every deposit and withdrawal.


4.  **Winner Number Calculation**

    * At contest end, a random number between 0 and `totalPerSecUserDeposit` is generated on-chain to select the winner.
    * The winner number can be forced manually or automatically triggered with the next deposit or withdrawal.
    * The winning number is published on-chain, and winnings (3% of `totalPerSecUserDeposit`) are recorded as events.


5.  **Off-Chain Winner Calculation**

    * Conducted off-chain due to on-chain feasibility limitations.
    * **Logic**:
      * Uses deposit and withdrawal events to calculate `perUserPerSecDeposit` for each user.
      * Sorts these values by the first deposit to map them to the total `totalPerSecUserDeposit`.
      * Identifies which user's deposit corresponds to the on-chain random winning number.
    * The winning address is updated on-chain and in logs.
    * Winnings are added to user balances and available for withdrawal.
    * Winnings not yet withdrawn are treated as deposits and included in future contest calculations.


6.  **Future Plans**:

    Publish the winner calculation code to allow public verification.
