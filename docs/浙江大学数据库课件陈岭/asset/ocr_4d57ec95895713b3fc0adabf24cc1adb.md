# More features of XML Schema

+   - **Attributes specified by xs:attribute tag:**
+     - `<xs:attribute name = “account_number”/>`
+     - adding the attribute `use = “required”` means value must be specified

+   - **Key constraint:** “account numbers form a key for account elements under the root bank element:
+     ```xml
+     <xs:key name = “accountKey”>
+         <xs:selector xpath = “]bank/account”/>
+         <xs:field xpath = “account_number”/>
+     <xs:key>
+     ```

+   - **Foreign key constraint from depositor to account:**
+     ```xml
+     <xs:keyref name = “depositorAccountKey” refer=“accountKey”>
+         <xs:selector xpath = “]bank/depositor”/>
+         <xs:field xpath = “account_number”/>
+     <xs:keyref>
+     ```