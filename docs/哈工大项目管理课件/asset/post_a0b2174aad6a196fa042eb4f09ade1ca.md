
## Figure 4-1. Information Technology Planning Process

![](img/1db87b9b55fa1232e052e0dffad9e0c7_107_0.png)

## Methods for Selecting Projects

- There is usually not enough time or resources to implement all projects.
- Methods for selecting projects include:
  - Focusing on broad organizational needs.
  - Categorizing information technology projects.
  - Performing net present value or other financial analyses.
  - Using a weighted scoring model.
  - Implementing a balanced scorecard.

## Focusing on Broad Organizational Needs

- It is often difficult to provide strong justification for many IT projects, but everyone agrees they have a high value.
- “It is better to measure gold roughly than to count pennies precisely.”
- Three important criteria for projects:
  - There is a **need** for the project.
  - There are **funds** available for the project.
  - There is a strong **will** to make the project succeed.

## Categorizing IT Projects

- One categorization assesses whether the project provides a response to:
  - A problem
  - An opportunity
  - A directive
- Another categorization is based on the time it will take to complete a project or the date by which it must be done.
- Another categorization is the overall priority of the project.

## Financial Analysis of Projects

Financial considerations are often an important aspect of the project selection process.

Three primary methods for determining the projected financial value of projects:

- Net present value (NPV) analysis
- Return on investment (ROI)
- Payback analysis

## Net Present Value Analysis

- **Net present value** (NPV) analysis is a method of calculating the expected net monetary gain or loss from a project by discounting all expected future cash inflows and outflows to the present point in time.
- Projects with a positive NPV should be considered if financial value is a key criterion.
- The higher the NPV, the better.

## Figure 4-2. Net Present Value Example

|   | A | B | C | D | E | F | G |
|---|---|---|---|---|---|---|---|
| 1 | Discount rate | 10% |  |  |  |  |  |
| 2 |  |  |  |  |  |  |  |
| 3 | PROJECT 1 | YEAR 1 | YEAR 2 | YEAR 3 | YEAR 4 | YEAR 5 | TOTAL |
| 4 | Benefits | $0 | $2,000 | $3,000 | $4,000 | $5,000 | $14,000 |
| 5 | Costs | $5,000 | $1,000 | $1,000 | $1,000 | $1,000 | $9,000 |
| 6 | Cash flow | ($5,000) | $1,000 | $2,000 | $3,000 | $4,000 | $5,000 |
| 7 | NPV → $2,316 |  |  |  |  |  |  |
| 8 | Formula =npv(b1,b6:f6) |  |  |  |  |  |  |
| 9 |  |  |  |  |  |  |  |
| 10 | PROJECT 2 | YEAR 1 | YEAR 2 | YEAR 3 | YEAR 4 | YEAR 5 | TOTAL |
| 11 | Benefits | $1,000 | $2,000 | $4,000 | $4,000 | $4,000 | $15,000 |
| 12 | Costs | $2,000 | $2,000 | $2,000 | $2,000 | $2,000 | $10,000 |
| 13 | Cash flow | ($1,000) | $0 | $2,000 | $2,000 | $2,000 | $5,000 |
| 14 | NPV → $3,201 |  |  |  |  |  |  |
| 15 | Formula =npv(b1,b13:f13) |  |  |  |  |  |  |
| 16 |  |  |  |  |  |  |  |

Note that totals are equal, but NPVs are not because of the time value of money.

## Figure 4-3. JWD Consulting NPV Example

Multiply by the discount factor each year, then subtract costs from cumulative benefits to get NPV.

| Discount rate | 8% |  |  |  |  |  |
| Assume the project is completed in Year 0 | Year |  |  |  |  |  |
|  | 0 | 1 | 2 | 3 | Total |  |
| Costs | 140,000 | 40,000 | 40,000 | 40,000 |  |  |
| Discount factor | 1 | 0.93 | 0.86 | 0.79 |  |  |
| Discounted costs | 140,000 | 37,200 | 34,400 | 31,600 | 243,200 |  |
|  |  |  |  |  |  |  |
| Benefits | 0 | 200,000 | 200,000 | 200,000 |  |  |
| Discount factor | 1 | 0.93 | 0.86 | 0.79 |  |  |
| Discounted benefits | 0 | 186,000 | 172,000 | 158,000 | 516,000 |  |
|  |  |  |  |  |  |  |
| Discounted benefits - costs | (140,000) | 148,800 | 137,600 | 126,400 | 272,800 ← NPV |  |
| Cumulative benefits - costs | (140,000) | 8,800 | 146,400 | 272,800 |  |  |
| ROI | 112% |  |  |  |  |  |
|  | Payback In Year 1 |  |  |  |  |  |

Note: See the template called business_case_financials.xls.
