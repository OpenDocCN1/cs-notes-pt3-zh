# # FLWOR Syntax in XQuery

+   - For clause uses XPath expressions, and variable in for clause ranges over values in the set returned by XPath

+   - Simple FLWOR expression in XQuery

+   - find all accounts with balance > 400, with each result enclosed in an `<account_number> .. </account_number>` tag

```
```
for $x in /bank-2/account
let $acctno := $x/@account_number
where $x/balance > 400
return <account_number> { $acctno }
</account_number>
```
```

+   - Items in the return clause are XML text unless enclosed in {}, in which case they are evaluated

+   - Let clause not really needed in this query, and selection can be done In XPath. Query can be written as:

```
```
for $x in /bank-2/account[balance>400]
return <account_number> { $x/@account_number }
</account_number>
```
```