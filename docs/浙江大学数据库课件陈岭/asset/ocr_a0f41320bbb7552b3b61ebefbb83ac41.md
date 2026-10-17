# # Nested Queries

+   - The following query converts data from the flat structure for bank information into the nested structure used in bank-1
+   <bank-1> {
+   for $c in /bank/customer
+   return
+   <customer>
+   { $c/* }
+   { for $d in /bank/depositor[customer_name = $c/customer_name],
+   $a in
+   /bank/account[account_number=$d/account_number]
+   return $a }
+   </customer>
+   } </bank-1>

+   - $c/* denotes all the children of the node to which $c is bound, without the enclosing top-level tag

+   - $c/text() gives text content of an element without any subelements / tags