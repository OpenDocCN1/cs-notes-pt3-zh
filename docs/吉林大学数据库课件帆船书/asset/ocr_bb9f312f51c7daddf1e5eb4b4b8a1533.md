# Snapshot Write: First Committer Wins

X₀ = 100

| T₁ deposits 50 in X | T₂ withdraws 50 from X |
|---|---|
| r₁(X₀, 100) | r₂(X₀, 100) |
|  | w₂(X₂, 50) |
| w₁(X₁, 150) |  |
| commit₁ | commit₂ (Serialization Error T₂ is rolled back) |

X₁ = 150

+   Variant: “First-updater-wins”
+   - Check for concurrent updates when write occurs by locking item
+     - But lock should be held till all concurrent transactions have finished
+   - (Oracle uses this plus some extra features)
+   - Differs only in when abort occurs, otherwise equivalent