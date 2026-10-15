# Simulating TM by URM

Suppose 𝓜 is a 3-tape TM with the alphabet {0,1,□,▷}.

The URM that simulates 𝓜 can be designed as follows:

+   - Suppose that Rₘ is the right most register that is used by a program calculating x -1.

+   - The head positions are stored in Rₘ₊₁, Rₘ₊₂, Rₘ₊₃.

+   - The three binary strings in the tapes are stored respectively in Rₘ₊₄, Rₘ₊₇, Rₘ₊₁₀, …, Rₘ₊₅, Rₘ₊₈, Rₘ₊₁₁, …, Rₘ₊₆, Rₘ₊₉, Rₘ₊₁₂, …

+   - The states of 𝓜 are encoded by the states of the URM.

+   - The transition function of 𝓜 can be easily simulated by the program of the URM.