ACID (Atomicity, Consistency, Isolation, Durability) are a set of properties that ensure the reliability and consistency of transactions in a database management system. Here are the ACID properties explained with examples:

1. **Atomicity:**
   - **Definition:** Atomicity ensures that a transaction is treated as a single unit, either all of its operations are performed, or none are.
   - **Example:** Consider a bank transfer where money is withdrawn from one account and deposited into another. If the deposit operation succeeds but the withdrawal fails, the system should ensure that both operations are rolled back, leaving the accounts in a consistent state.

2. **Consistency:**
   - **Definition:** Consistency ensures that a transaction brings the database from one valid state to another. It enforces integrity constraints and business rules.
   - **Example:** In a database that enforces a constraint that all employees must have a manager, if a transaction attempts to assign an employee to a department without a manager, it would be rejected, ensuring consistency.

3. **Isolation:**
   - **Definition:** Isolation ensures that multiple transactions can be executed concurrently without interfering with each other.
   - **Example:** Consider two transactions that both attempt to withdraw money from an account. Isolation ensures that one transaction's operations do not interfere with the other, and they are executed independently.

4. **Durability:**
   - **Definition:** Durability guarantees that once a transaction is committed, the changes it made to the database persist even in the event of a system failure.
   - **Example:** If a transaction successfully updates a database, the changes must be stored permanently. Even if the system crashes immediately after the commit, when it recovers, the changes made by the transaction should still be present in the database.

Here's a simplified example to illustrate these properties:

Let's say you have a banking application:

1. **Atomicity Example:**
   - Transaction: Transfer $100 from Account A to Account B.
   - If the system fails after debiting Account A but before crediting Account B, atomicity ensures that both operations are rolled back.

2. **Consistency Example:**
   - Constraint: All accounts must have a positive balance.
   - Transaction: Attempt to transfer $100 from Account A to Account B when both accounts have $50.
   - The system should reject the transaction, maintaining consistency.

3. **Isolation Example:**
   - Transaction 1: Transfer $100 from Account A to Account B.
   - Transaction 2: Transfer $50 from Account B to Account C.
   - Isolation ensures that the operations in Transaction 1 do not interfere with Transaction 2, even if they are executed concurrently.

4. **Durability Example:**
   - Transaction: Transfer $100 from Account A to Account B (successfully committed).
   - Even if the system crashes immediately after committing the transaction, when it restarts, the changes made by the transaction should still be present in the database.

These examples demonstrate how the ACID properties ensure the reliability and integrity of transactions in a database system.
