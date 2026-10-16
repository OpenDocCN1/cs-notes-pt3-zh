
## Information Model

- Data can be imported in from existing sources or upon export be used to help develop or enhance systems.
- Ability to associate critical information required for the process execution and to support the logic behind how the process behaves.
- Used in the analysis model for dynamic analysis of the process

## Customer Application

Parent template None

### Business item attributes

Attributes are properties or significant features. Inherited attributes can be edited in the parent definition.

| Name |  | Type |
|---|---|---|
| applicationName | ✓ | String |
| companyName | ✓ | String |
| customerAddress1 | ✓ | String |
| customerAddress2 | ✓ | String |
| customerCity | ✓ | String |
| customerState | ✓ | String |
| customerCountry | ✓ | String |
| customerPostalCode | ✓ | String |
| contactFirstName | ✓ | String |
| contactLastName | ✓ | String |
| contactPhoneNumber | ✓ | String |
| requestAccountAmount | ✓ | String |
| creditReportNeeded |  | Boolean |
| creditScore |  | Integer |
| productName |  | String |
| pricingCode |  | Integer |
| applicationDecision |  | Boolean |
| comments |  | String |

Add Remove Move Up Move Down

### Attribute details

Edit the details of the selected attribute. Inherited attributes can only be edited in the parent definition.

### Attribute description

If a credit report is older than N number of months (business rule will be used to set this dynamically) on a credit report will be needed. [T...]

Templates can be used to inherit information that was modeled previously or that are reusable across business items

Rules associated to business items can be evaluated during analysis

Change Icon...

Attributes Documentation

## Resource Model

- Defines all role, individual, and bulk resources that are used within the business process and their associated costs
- Complex resource behaviors can be modeled in order to accurately reflect those behaviors in the analysis model

## Business Modeling

### Account Coordinator

### Account Coordinator 1

### Scope dimension

Use this section to add scope dimensions. A scope dimension defines and measures specific qualities and requirements for a role.

### Scope dimension details

Details of the selected scope dimension.

### Scope dimension value type

Language Spoken

String

### Instance of

### Resource attributes

Attributes of the resource definition. If the resource definition is updated, refresh the table to synchronize this resource with the resource definition.

### Selected attribute values

Use this section to edit values for an attribute with a maximum occurrence greater than 1.

| Name | Type |
|------|------|
| personID | String |
| lastName | String |
| firstName | String |
| profile | String |
| email | String |
| phone | String |
| employeeID | String |
| taxPayerID | String |
| fax | String |
| timezone | String |
| secretary | String |
| assistant | String |
| manager | String |
| company | String |
| department | String |
| middleName | String |

Scope definition helps identify specialized resource skill required to complete the steps in a business process

Costs can be associated to resources and can be both per time unit and any one time start up costs

Specifying availability characteristics assists in simulating real scenarios of resource constraints

- Business items
- Processes
- Resources
  - Account Coordinator
  - Account Manager
  - Credit Management Service
  - Decision Mgmt System
  - Eligibility System
  - Software
    - Account Coordinator 1
    - Account Coordinator 2
    - Account Coordinator 3
    - Account Coordinator 4
    - Account Coordinator 5
    - Account Manager 1
    - Account Manager 2
  - IBM Software
  - 24Hour
  - Day Shift
  - Day Shift
  - Saturday
  - Sunday
- Organizations
- Classifier
- Classifiers
- Reports
- Queries
- Predefined resources
- Predefined organizations
- Predefined classifiers

Scope dimension Costs Availability Documentation

Costs Availability Qualifications Attributes Documentation
