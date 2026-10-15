
The review process consists of five formal steps:

- In the **overview** step, the author of the module gives a presentation to the team.
- In the **preparation** step, the participants try to understand the code in detail and compile lists of issues, ranked in order of severity(严重性). They are aided in this process by a checklist of potential faults for which to be on the lookout.
- In the **inspection** step, a thorough walkthrough of the code is performed, aiming for fault detection through complete coverage of the code. Within a day of the inspection, the moderator produces a meticulous（小心翼翼）written report.
- In the **rework** step, the individual responsible for the code resolves all faults and issues noted in the written report. （Individual Reviewer Issues Spreadsheet）
- In the **follow-up** step, the moderator must make sure that each issue has been resolved by either fixing the code or clarifying confusing points. （Review Report Spreadsheet）

## Individual Reviewer Issues Spreadsheet

| <Work product information> |  |  |  |  |
| <Reviewer Name> |  |  |  |  |
| <Preparation Date> |  |  |  |  |
| <Reviewer Preparation Time> |  |  |  |  |
|  | Location | Checklist |  |  |
| Issue # | Page | Line | Item | Severity | Description |
| 1 | 1 | 18 | Typo | 1 | Change "accound" to "account" |

## Review Report Spreadsheet

| Review Team Members | Preparation Time | |
|---|---|---|
| Leader | | |
| Recorder | | |
| Reviewer | | |
| Reviewer | | |
| Reviewer | | |
| Reviewer | | |
|  | Total prep time | |
| Meeting date | | |

<Review Recommendation>

| Issue # | Reviewer | Location |  | Checklist |  | Description |
|---|---|---|---|---|---|---|
|  |  | Page | Line | Item | Severity |  |
| 1 |  | 1 | 18 | Typo | 1 | Change “accord” to “account” |

- An important product of an inspection is the number and kinds of faults found rated by severity. ([Here is a sample outline of a review report](#))
- If a module comes through an inspection exhibiting a significantly larger number of faults than other modules in the system, it is a good candidate for rewriting.
- If the inspection of two or three modules reveals a large number of errors of specific types, this may warrant (re)checking other modules for similar errors.
- If more than 5 percent of the material inspected must be reworked, the team must reconvene for a full re-inspection.

## 3.2 Execution-based Verification

Use test cases to execute the program, get all results from the execution.

There are two basic approaches to testing modules, each with its own weaknesses.

- Testing to Specifications, also known as black-box test.
- Testing to Code, also called glass-box, white-box test.

### 3.2.1 Black-box test

![](img/8454895dcf92bedbe5b40d0487077d64_116_0.png)

- Seeks to verify that the module conforms to the specified input and output while ignoring the actual code
- It is rarely possible to test all modules for all possible input cases, which may be a huge number of modules

- Equivalence testing is a technique based on the idea that the input specifications give ranges of values for which the software product should work the same way.
- Boundary value analysis seeks to test the product with input values that lie on and just to the side of boundaries between equivalence classes.

For example the input is (a,b), there are at least 5 equivalence classes:

![](img/8454895dcf92bedbe5b40d0487077d64_118_0.png)

**functional testing**, the tester identifies each item of functionality or each function implemented in the module and uses data to test each function.

### 3.2.2 White-box test

![](img/8454895dcf92bedbe5b40d0487077d64_119_0.png)

- Also called logic-driven, or path-oriented testing.
- testing each path through the code is generally not feasible, even for simple flowcharts.
- Moreover, it is possible to test every path without finding existing faults, because, for example, the fault lies in the decision criterion for selecting between paths.
