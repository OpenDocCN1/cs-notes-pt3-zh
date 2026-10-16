# Regular expressions

For the purpose of using GNFA to prove the next theory, we require that GNFA always have the following special form:

+   The start state has transition arrows going to every other state but no arrows coming in from any other state.

+   There is only a single accept state, and it has arrows coming in from every other state but no arrows going to any other state. Further more, the accept state is not the same as the start state.

+   Except for the start and accept states, one arrow goes from every state to every other state and also from each state to itself.