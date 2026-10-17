# Example Queries

+   - Example 1: Find all customers who have an **account** from **at least** the “Downtown” and the “Uptown” branches.

**Query 1**

\[\Pi_{CN}(\sigma_{BN=\text{“Downtown”}}(depositor \bowtie account))\]
\[\Pi_{CN}(\sigma_{BN=\text{“Uptown”}}(depositor \bowtie account))\]

where **CN** denotes customer-name and **BN** denotes *branch-name*.

**Query 2**

\[\Pi_{customer-name,\ branch-name}(depositor \bowtie account)\]
\[\div\ \rho_{temp(branch-name)}(\{(\text{“Downtown”}),\ (\text{“Uptown”})\})\]