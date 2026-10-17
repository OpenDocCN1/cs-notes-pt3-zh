# Explicit Cursor Attributes

Obtain status information about a cursor.

| Attribute | Type | Description |
|---|---|---|
| %ISOPEN | Boolean | Evaluates to TRUE if the cursor is open. |
| %NOTFOUND | Boolean | Evaluates to TRUE if the most recent fetch does not return a row. |
| %FOUND | Boolean | Evaluates to TRUE if the most recent fetch returns a row; complement of %NOTFOUND |
| %ROWCOUNT | Number | Evaluates to the total number of rows returned so far. |