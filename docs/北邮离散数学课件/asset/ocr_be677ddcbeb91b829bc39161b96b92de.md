# Representing Sets with Bit Strings

For an enumerable u.d. *U* with ordering  
*x₁, x₂, …*, represent a finite set S⊆U as  
the finite bit string B=*b₁b₂…bₙ* where

∀i: xᵢ∈S ↔ (i≤n ∧ bᵢ=1).

*E.g.* U=ℕ, S={2,3,5,7,11},  
B=001101010001.

In this representation, the set operators “∪”, “∩”, “¯” are implemented directly  
by bitwise OR, AND, NOT!