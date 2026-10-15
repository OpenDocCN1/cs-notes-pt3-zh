# Decidable Predicate

A predicate $R(\bar{x})$ is decidable if its characteristic function

$c_R(\bar{x}) \stackrel{\text{def}}{=} \begin{cases} 1, & \text{if } R(\bar{x}) \text{ is true}, \\ 0, & \text{otherwise.} \end{cases}$

is a recursive function. The predicate $R(\bar{x})$ is partially decidable if its partial characteristic function

$\chi_R(\bar{x}) \stackrel{\text{def}}{=} \begin{cases} 1, & \text{if } R(\bar{x}) \text{ is true}, \\ \uparrow, & \text{otherwise.} \end{cases}$

is a recursive function.