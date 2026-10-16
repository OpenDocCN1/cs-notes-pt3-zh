
# The controller for an automatic door

![](img/505b35cb28b35d38fc29ccba74c23087_54_0.png)

Top view of the system

# The controller for an automatic door

![](img/505b35cb28b35d38fc29ccba74c23087_55_0.png)

State diagram

# The controller for an automatic door

| state | NEITHER | FRONT | REAR | BOTH |
|---|---|---|---|---|
| CLOSED | CLOSED | OPEN | CLOSED | CLOSED |
| OPEN | CLOSED | OPEN | OPEN | OPEN |

Transition table of the door

# The controller for an automatic door

# Example:

- Start in state **closed**
- Receive the series of input signals FRONT, REAR, NEITHER, FRONT, BOTH, NEITHER, REAR and NEITHER,
- Controller will go through the series of states CLOSED (starting), OPEN, OPEN, CLOSED, OPEN, OPEN, CLOSED, CLOSED, AND CLOSED

# Finite Automata (FA)

- The daily devices that can be demonstrated by FA
  - Accutron (electronic watch):
    - e.g: there four keys on the Accutron, then there are four possible input, and there are some states.
  - Recorder: the transform keys:
    - ▶. ▶▶. ◀◀. ○. ■ are the possible input.
  - TV telecontrol
    - the telecontrol of multilayer menu.
  - Elevator

# Finite Automata

- Briefly, FA:
  - Current State + Input → Next State
- As a computer, FA:
  - can read
  - can not write
  - no memory (only register to store states and input)
  - can not perform reasoning
  - no imagination
  - That is, computation here is to judge the last state.

# Finite Automata

# State diagram:

We use M₁ to denote a FA (NFA: uses N₁)

- States:
  - 3 states: q₁, q₂, q₃

- Start state:
  - indicated by the arrow pointing at it from nowhere :e.g. q₁

- Accept state:
  - the one with a double circle. e.g.: q₂

- Inputs:
  - Strings: a finite list of symbols from alphabet Σ

- Transitions
  - The arrows going from one state to another

- Output:
  - Accept or reject

![](img/505b35cb28b35d38fc29ccba74c23087_60_0.png)

# Finite Automata

- **The process procedure:**
  - Begins in $M_1$'s **start state**
  - Repeat until the last symbol:
    - Read one **symbol** from the input string from left to right in turns.
    - $M_1$ moves from one state to another along the **transition** that has that symbol as its label.
  - $M_1$ produces its output, the output is **accept** if $M_1$ is now in an accept state and **reject** if it is not.

# Finite Automata

E.g.: We input a string 1101 to the FA M₁

The processing proceeds:

- Start in state q₁.
- Read 1, follow transition from q₁ to q₂;
- Read 1, follow transition from q₂ to q₂;
- Read 0, follow transition from q₂ to q₃;
- Read 1, follow transition from q₃ to q₂.
- Accept because M₁ is in an accept state q₂ at the end of the input.

In fact, M₁ accepts any string that ends with a 1, and also any string that ends with an even number of 0s following the last 1.

![](img/505b35cb28b35d38fc29ccba74c23087_62_0.png)

# Formal Definition of FA

- A finite automaton is a 5-tuple ($Q$, $\Sigma$, $\delta$, $q_0$, $F$), where
  1. $Q$ is a finite set called the states,
  2. $\Sigma$ is a finite set called the alphabet,
  3. $\delta : Q \times \Sigma \rightarrow Q$ is the transition function
  4. $q_0 \in Q$ is the start state, and
  5. $F \subseteq Q$ is the set of accept states.

- Transition function is denoted by $\delta$
  - $\delta(x, 1) = y$ means there is a arrow from a state $x$ to a state $y$ labeled with the input symbol 1.

# Formal Definition of FA

E.g. we formally describe M₁ as following:

M₁ = (Q, Σ, δ, q₁, F), where

- 1. Q = {q₁, q₂, q₃}
- 2. Σ = {0, 1}
- 3. δ is described as
- 4. q₁ is the start state, and
- 5. F = {q₂}

|   | 0 | 1 |
|---|---|---|
| q₁ | q₁ | q₂ |
| q₂ | q₃ | q₂ |
| q₃ | q₂ | q₂ |

![](img/505b35cb28b35d38fc29ccba74c23087_64_0.png)

# Formal Definition of FA

- If $A$ is the set of all strings that machine $M$ accepts, we say that $A$ is the language of machine $M$, or $M$ recognizes $A$.

  $L(M)=A$
- If the machine accepts no strings, it still recognizes one language:

  empty language $\emptyset$
- E.g.:
  - $A = \{w\mid w \text{ contains at least one 1 and also an even number of 0s follow the last 1}\}$, Then

    $L(M)=A$, or $M$ recognizes $A$.
