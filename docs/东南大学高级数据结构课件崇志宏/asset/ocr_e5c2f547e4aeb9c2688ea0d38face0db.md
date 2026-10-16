# Final Results

+   - Zipflan Distribution: m_i ∝ 1/i^α [Power Law]

+   - FindApproxTop
+     - [k + (Σ_{i>k} m_i²) / (ε m_k)²] log m/δ
+     - Roughly: sampling bound with frequencies squared
+     - Zipfian – gives improved results

+   - FindCandidateTop
+     - Zipf parameter 0.5
+     - O(k log N log m)
+     - Compare: sampling bound O((kN)^0.5 log k)