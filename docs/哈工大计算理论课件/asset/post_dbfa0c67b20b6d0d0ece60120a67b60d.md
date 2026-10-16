
## Circuit Complexity

### Definition
- A Boolean Circuit is a collection of gates and inputs connected by wires.
- Cycles are not permitted
- Gates take three forms
  - AND gate
  - OR gate
  - Not gate

![](img/505b35cb28b35d38fc29ccba74c23087_818_0.png)

- Wires in a Boolean circuit carry the Boolean values 0 and 1
- The gates are simple processors that compute the Boolean functions AND, OR and NOT.
- Inputs are labeled $x_1, ..., x_n$
- One of the gates is designated as the output gate

![](img/505b35cb28b35d38fc29ccba74c23087_819_0.png)

- A Boolean circuit computes an output value from a setting of the inputs by propagating values along the wires and computing the function associated with the respective gates until the output gate is assigned a value

![](img/505b35cb28b35d38fc29ccba74c23087_820_0.png)

- We use functions to describe the input/output behavior of Boolean circuits. To a Boolean circuit $C$ with n input variables, we associate a function $f_C$: $\{0,1\}^n \to \{0,1\}$, where if $C$ outputs $b$ when its inputs $x_1,\dots,x_n$ are set to $a_1,\dots,a_n$, we write $f_C(a_1,\dots,a_n)=b$
- $C$ computes the function $f_C$
- If we have $k$ outputs, the range of $f_C$ is $\{0,1\}^k$
- Then, we look at the $n$-input parity function $parity_n$: $\{0,1\}^n \to \{0,1\}$.

- $parity_4$

![](img/505b35cb28b35d38fc29ccba74c23087_822_0.png)

- One may observe that we need to fix the number of variables beforehand in circuit design
- But TM takes arbitrary length of input string and may different every time
- So, we design a circuit for particular input length for testing the membership of a language
- Then, we have a family of circuits, one for each input length

### Definition
- A **circuit family** $C$ is an infinite list of circuits, $(C_0, C_1, C_2, ...)$, where $C_n$ has n input variables
- We say that $C$ decides a language $A$ over $\{0,1\}$ if for every string $w$

  $w \in A \quad \text{iff} \quad C_n(w)=1$

  where n is the length of $w$

- The **size** of a circuit is the number of gates that it contains
- Two circuits are **equivalent** if they have the same input variables and output the same value on every input assignment
- A circuit size is **minimal** if no smaller circuit is equivalent to it
- A circuit family for a language is minimal if every $C_i$ is minimal
- Finding the minimal circuit may not be solvable in N or NP

- **Size complexity** of a circuit family ($C_0$, $C_1$, $C_2$,...) is a function $f$: $N \rightarrow N$, where $f(n)$ is the size of $C_n$
- **Depth** of a circuit is the length (number of wires) of the longest path from an input variable to the output gate.
- Definition of **depth minimal** and **depth complexity** are similar to the one for circuit size, but use depth to instead of size
- **Circuit size complexity of a language** is the size complexity of a minimal circuit family for that language.
- Circuit depth complexity is defined similar to size’s

- The circuit complexity of a language is related to its time complexity
- **Theorem**
  - Let $t: N \to N$ be a function, where $t(n) \ge n$
  - If $A \in \text{TIME}(t(n))$, then $A$ has a circuit complexity $O(t^2(n))$
- This theorem gives an approach to proving that P is not equal to NP whereby we attempt to show that some language in NP has more than polynomial circuit complexity

- Proof Idea:
  - Let M be a TM that decides A in time t(n), we ignore O(t(n)) for simplicity
  - For each n we construct a circuit Cₙ that simulates M on inputs of length n
  - The gates of Cₙ are organized in rows, one for each of the t(n) step in M’s computation on an input of length n
  - Each row of gates represents the configuration of M at the corresponding step
  - Each row is wired into the previous row so that it can calculate its configuration from previous row’s configuration
