# # Three common cases

Compare _f_(_n_) with _n_log_ba_ :

+   1. _f_(_n_) = _O_(_n_log_ba_ - ε) for some constant ε > 0.
+      • _f_(_n_) grows polynomially slower than _n_log_ba_ (by an _n_ε factor).
+      **Solution:** _T_(_n_) = Θ(_n_log_ba_) .

+   2. _f_(_n_) = Θ(_n_log_ba_ lg_kn_) for some constant _k_ ≥ 0.
+      • _f_(_n_) and _n_log_ba_ grow at similar rates.
+      **Solution:** _T_(_n_) = Θ(_n_log_ba_ lg<sup>_k_+1</sup>_n_) .