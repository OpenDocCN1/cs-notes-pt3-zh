![](bbox=[0.0, 0.02, 0.09, 0.16])

# Multiversion Timestamp Ordering

+   Each data item Q has a sequence of versions <Q₁, Q₂,..., Qₘ>. Each version Qₖ contains three data fields:

+   - **Content** -- the value of version Qₖ.

+   - **W-timestamp(Qₖ)** -- timestamp of the transaction that created (wrote) version Qₖ

+   - **R-timestamp(Qₖ)** -- largest timestamp of a transaction that successfully read version Qₖ

+   When a transaction Tᵢ creates a new version Qₖ of Q, Qₖ's W-timestamp and R-timestamp are initialized to TS(Tᵢ).

+   R-timestamp of Qₖ is updated whenever a transaction Tⱼ reads Qₖ, and TS(Tⱼ) > R-timestamp(Qₖ).