

## 6.1 Attributes and attribute grammars

- **Binding** of the attribute: the process of computing an attribute and associating its computed value with the language construct in question.
- **Binding time**: the time during the compilation/execution process when the binding of an attribute occurs.

- Binding times of different attributes vary, and even the same attributes that can have quite different binding times from language to language.

- **Static attributes/Dynamic attributes:** Based on the difference of the binding time
  - be bound prior to execution
  - be bound during execution

![](img/1db31d392048feae2d803578b3d5a4b9_372_0.png)

![](img/1db31d392048feae2d803578b3d5a4b9_372_1.png)

- A type checker: is an important part of semantic analysis (in a language like C or Pascal)

- A type checker is a analyzer

- ➤ computes the data type attribute of all language entities for which data types are defined

- ➤ verifies that these types conform to the type rules of the language.

- Type checking = set of rules that ensure the type consistency of different constructs in the program

- Examples:

- The type of a variable must match the type from its declaration

- The operands of arithmetic expressions (+, *, -, /) must have integer types; the result has integer type

- The operands of comparison expressions (==, !=) must have integer or string types; the result has boolean type

![](img/1db31d392048feae2d803578b3d5a4b9_374_0.png)

### More examples:

> For each assignment statement, the type of the updated variable must match the type of the expression being assigned

> For each call statement foo(v1, ..., vn), the type of each actual argument vi must match the type of the corresponding formal argument fi from the declaration of function foo

> The type of the return value must match the return type from the declaration of the function

![](img/1db31d392048feae2d803578b3d5a4b9_375_0.png)

![](img/1db31d392048feae2d803578b3d5a4b9_375_1.png)

## 6.1.1 Attribute grammars

X.a : the value of a associated to X  
X is a grammar symbol and a is an attribute associated to X.

syntax-directed semantics: attributes are associated directly with the grammar symbols of the language.

Given attributes a₁, a₂, ... , aₖ, for each grammar rule X₀→X₁ X₂ ... Xₙ ( X₀ is a nonterminal ), the values of the attributes Xᵢ.aⱼ of each grammar symbol Xᵢ are related to the values of the attributes of the other symbols in the rule.

• An attribute grammar for attributes a₁, a₂, ... , aₖ is the collection of all attribute equations or semantic rules of the following form, for all the grammar rules of the language.
Xᵢ.aⱼ=fᵢⱼ(X₀.a₁,...,X₀.aₖ, X₁.a₁, ..., X₁.aₖ,...Xₙ.a₁, ...Xₙ.aₖ)
fᵢⱼ is a mathematical function of its arguments

attribute grammars are written in tabular form as follows:

| Grammar Rule | Semantic Rules |
|---|---|
| Rule 1 | Associated attribute equations |
| ..... | .......... |
| .......... | ............ |
| ... | . |
| Rule n | Associated attribute equations |

![](img/1db31d392048feae2d803578b3d5a4b9_378_0.png)

![](img/1db31d392048feae2d803578b3d5a4b9_378_1.png)

### Example 6.1:

Number → number digit | digit

Digit → 0|1|2|3|4|5|6|7|8|9

| Grammar Rule | Semantic Rules |
|---|---|
| number1 → number2 digit | number1.val = number2.val*10+digit.val |
| number → digit | number.val = digit.val |
| digit → 0 | digit.val = 0 |
| digit → 1 | digit.val = 1 |
| digit → 2 | digit.val = 2 |
| digit → 3 | digit.val = 3 |
| digit → 4 | digit.val = 4 |
| digit → 5 | digit.val = 5 |
| digit → 6 | digit.val = 6 |
| digit → 7 | digit.val = 7 |
| digit → 8 | digit.val = 8 |
| digit → 9 | digit.val = 9 |

![](img/1db31d392048feae2d803578b3d5a4b9_379_0.png)

![](img/1db31d392048feae2d803578b3d5a4b9_379_1.png)

