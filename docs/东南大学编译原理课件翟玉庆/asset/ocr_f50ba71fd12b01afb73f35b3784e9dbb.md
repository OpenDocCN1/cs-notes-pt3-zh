# CHAPTER 4  SYNTAX ANALYSIS

# Section 5  LR parsers

# 14、Valid LR(1) item

Formally, we say LR(1) item (A→α•β,a) is valid for a viable prefix γ if there is a derivation S`→δαω→δαβω, where

+   - γ=δα, and
+   - Either a is the first symbol of ω, or ω is ε and a is $.