# The Halting problem is undecidable

+   - Construct a new TM *D* with *H* as a subroutine.

+   - *D* = “On input ⟨*M*⟩, where *M* is a TM

+   1. Run *H* on input ⟨*M*, ⟨*M*⟩⟩.

+   2. Output the opposite of what *H* outputs; that is, if *H* accepts, *reject* and if *H* rejects, *accept*.”

In summary:

$$D(\langle M\rangle)=\begin{cases}accept & \text{if } M \text{ does not accept } \langle M\rangle \\ reject & \text{if } M \text{ accept } \langle M\rangle\end{cases}$$