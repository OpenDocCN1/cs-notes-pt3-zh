# Example of Turing machine

+   3. Cross off an *a* and scan to the right until *ab* occurs. Shuttle between the *b*’s and the *c*’s, crossing off one of each until all *b*’s are gone. If all *c*’s have been crossed off and some *b*’s remain, *reject*.

+   4. Restore the crossed off *b*’s and repeat stage 3 if there is another *a* to across off. If all *a*’s have been crossed off, determine whether all *c*’s also have been crossed off. If yes, *accept*; otherwise, *reject*.”