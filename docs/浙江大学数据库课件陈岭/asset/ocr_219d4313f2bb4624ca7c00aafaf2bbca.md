# # XML Schema Version of Bank DTD

+   - Choice of “xs:” was ours - any other namespace prefix could be chosen

+   - Element “bank” has type “BankType”, which is defined separately

+   - xs:complexType is used later to create the named complex type “BankType”

+   - Element “account” has its type defined in-line