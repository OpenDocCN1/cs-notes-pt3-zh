# Minimal length descriptions

Theorem: ∃c∀x, y [K(xy) ≤ 2K(x) + K(y) + c]
Proof:

+   - Construct TM M that breaks its input w into two separate descriptions. The bits of the first description d(x) are all doubled and terminated with string 01. the second description d(y) stays. Run the corresponding machine to output string xy.

+   - Obviously the length of description of xy is twice the complexity of x plus the complexity of y plus a fixed constant for describing M.

2K(x) + K(y) + c