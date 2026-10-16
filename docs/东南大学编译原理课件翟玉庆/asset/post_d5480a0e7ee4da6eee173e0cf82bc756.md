
## Chapter 9 Code optimization

### Section 4 Data-flow analysis

```
for each block B do {
    IN[B] = ∅;
    OUT[B] = GEN[B];
}
change = true;
while change do {
    change = false;
    for each block B do {
        IN[B] = ⋃_{P ∈ pred(B)} OUT[P];
        oldout = OUT[B];
        OUT[B] = IN[B] - KILL[B] ∪ GEN[B];
        if OUT[B] != oldout
            change = true;
    }
}
```

### 5. Live-Variable Analysis

- In live-variable analysis, we wish to know for variable x and point p whether the value of x at p could be used along some path in the flow graph starting at p.
- If so, we say x is live at p; otherwise x is dead at p.

L.IN[B] = (L.OUT[B] - L.DEF[B]) ∪ L.USE[B]

L.OUT[B] = ⋃_{S ∈ succ(B)} L.IN[S]

succ(B) is the set of successors of B.

### 6. Live-Variable Algorithm

- Input. A flow graph with L.DEF and L.USE computed for each block.
- Output. L.OUT[B], the set of variables live on exit from each block B of the flow graph.
- Method.

```
for each block B do {
    L.OUT[B] = ∅;
    L.IN[B] = L.USE[B];
}
change = true;
while change do {
    change = false;
    for each block B do {
        L.OUT[B] = ⋃_{S ∈ succ(B)} L.IN[S];
        oldin = L.IN[B];
        L.IN[B] = (L.OUT[B] - L.DEF[B]) ∪ L.USE[B];
        if L.IN[B] != oldin
            change = true;
    }
}
```

### 7. Definition-Use Chains

- We say a variable is used at statement s if its r-value may be required.
- The du-chaining problem is to compute for a point p the set of uses s of a variable, say x, such that there is a path from p to s that does not redefine x.

## Description on Labs

### Task

Lab1: Lexical Analyzer Programming  
Lab2: Syntax Parser Programming

Notices:
1. The programming language is not limited (better C or Java).
2. You can finish the labs in any method in the suggested optional methods.
3. The complexity of lexical and syntactic definitions is decided by yourself.

### Requirements on Lab1

1. Input
   - Stream of characters
   - REs (the number of REs is decided by yourself)
2. Output
   - Sequence of tokens
3. Classes of words are defined by yourself
4. Error handling may be included

### Optional Implementing Methods on Lab1

1. Simulating programs in Section 2.6.5
2. Programming based on FA
   - a. Define some REs by yourself
   - b. Convert REs into NFAs
   - c. Merge these NFAs into a single NFA
   - d. Convert the NFA into a DFA with minimum states
   - e. Programming based on the DFA
3. Generating programs based on your own Lex
   - a. Design your own Lex
      - i. Define .l file
      - ii. Programming your own Lex
   - b. Generating programs based on your own Lex

### Requirements on Lab2

1. Input
   - Stream of characters
   - CFG (combination of CFGs of some classes of sentences)
2. Output
   - Sequence of derivations if top-down syntax analyzing methods are used.
   - Sequence of reductions if bottom-up syntax analyzing methods are used.
3. Classes of sentences are defined by yourself
4. Error handling may be included

### Optional Implementing Methods on Lab2

1. Recursive descent parsing
   - A non-terminal is related to a function/subroutine
2. LL(1)
   - a. Construct LL(1) parsing table based on the CFG
   - b. Design the program using LL(1) parsing table
3. LR(1)
   - a. Construct LR(1) parsing table based on the CFG
   - b. Design the program using LR(1) parsing table

## Lab Document Requirements

1. Reports on labs
   - a. Motivation/Aim
   - b. Content description
   - c. Ideas/Methods
   - d. Assumptions
   - e. Related FA descriptions
   - f. Description of important Data Structures
   - g. Description of core Algorithms
   - h. Use cases on running
   - i. Problems occurred and related solutions
   - j. Your feelings and comments
2. CD on labs
   - a. A CD is needed by a class for each lab
   - b. Each person is related to a directory in the CD
   - c. In the directory of a person, the following files are needed:
      - Input file
      - Output file
      - Source program files
      - Report file
      - Other related files
