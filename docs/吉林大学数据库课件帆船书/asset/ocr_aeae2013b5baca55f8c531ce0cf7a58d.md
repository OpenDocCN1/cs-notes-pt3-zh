# Data Representation

+   - Records in many big data applications need to have a flexible schema

+   - Not all records have same structure

+   - Some attributes may have complex substructure

+   - XML and JSON data representation formats widely used

+   - An example of a JSON object is:

```
{
  "ID": "22222",
  "name": {
    "firstname": "Albert",
    "lastname": "Einstein"
  },
  "deptname": "Physics",
  "children": [
    { "firstname": "Hans", "lastname": "Einstein" },
    { "firstname": "Eduard", "lastname": "Einstein" }
  ]
}
```