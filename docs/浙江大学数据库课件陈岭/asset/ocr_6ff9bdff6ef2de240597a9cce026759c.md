# Example Queries

+   - **Example 3:** Find the names of all customers who have a loan, **or** an account, or both, from the bank

$\Pi_{customer-name}(borrower) \cup \Pi_{customer-name}(depositor)$

+   - **Example 4:** Find the names of all customers who at least have a loan **and** an account at bank.

$\Pi_{customer-name}(borrower) \cap \Pi_{customer-name}(depositor)$

| Relation | Attributes |
|---|---|
| depositor | customer-name, account-number |
| borrower | customer-name, loan-number |