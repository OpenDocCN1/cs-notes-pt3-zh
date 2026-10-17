

## Bank DTD with Attributes

Bank DTD with ID and IDREF attribute types.

```xml
<!DOCTYPE bank-2 [
<!ELEMENT account (branch_name, balance)>
<!ATTLIST account
account_number ID # REQUIRED
owners IDREFS # REQUIRED>
<!ELEMENT customer(customer_name,
customer_street, customer_city)>
<!ATTLIST customer
customer_id ID # REQUIRED
accounts IDREFS # REQUIRED>
... declarations for branch_name, balance,
customer_name, customer_street and customer_city
] >
<! ELEMENT branch_name (#PCDATA)>
<! ELEMENT balance(#PCDATA)>
<! ELEMENT customer_name(#PCDATA)>
<! ELEMENT customer_street(#PCDATA)>
<! ELEMENT customer_city(#PCDATA)>
```

## XML data with ID and IDREF attributes

```xml
<bank-2>
  <account account_number="A-401" owners="C100 C102">
    <branch_name> Downtown </branch_name>
    <balance> 500 </balance>
  </account>
  <customer customer_id="C100" accounts="A-401">
    <customer_name>Joe </customer_name>
    <customer_street> Monroe </customer_street>
    <customer_city> Madison</customer_city>
  </customer>
  <customer customer_id="C102" accounts="A-401 A-402">
    <customer_name> Mary </customer_name>
    <customer_street> Erin </customer_street>
    <customer_city> Newark </customer_city>
  </customer>
</bank-2>
```

## Example

```xml
<bookstore>
  <book ISBN="7-04-011049-0">
    <title>Dadatabase System Concepts</title>
    <author>Abraham Silberschatz</author>
    <author>Henry F. Korth</author>
    <author>S.Sudarshan</author>
    <price>59.5</price>
  </book>
  <book ISBN="0-06-662099-6">
    <title>Good to Great</title>
    <author>Jim Collins</author>
    <price>88.9</price>
  </book>
</bookstore>
```

![](img/5b3fa86b6571b68f1313de4e5d81fe8a_608_0.png)

![](img/5b3fa86b6571b68f1313de4e5d81fe8a_608_1.png)

```xml
<!DOCTYPE bookstore [
<!ELEMENT bookstore ((book) + ) >
<!ELEMENT book ( title author * price ) >
<!ATTLIST book
ISBN ID #REQUIRED >
<!ELEMENT title ( #PCDATA ) >
<!ELEMENT author (#PCDATA )>
<!ELEMENT price ( #PCDATA ) >
] >
```

## Limitations of DTDs

- No typing of text elements and attributes
  - All values are strings, no integers, reals, etc.
- Difficult to specify unordered sets of subelements
  - Order is usually irrelevant in databases (unlike in the document-layout environment from which XML evolved)
  - `(A | B)*` allows specification of an unordered set, but cannot ensure that **each of A and B occurs only once**
- IDs and IDREFs are untyped
  - The _owners_ attribute of an account may contain a reference to another account, which is meaningless
    - owners attribute should ideally be constrained to refer to customer elements

![](img/5b3fa86b6571b68f1313de4e5d81fe8a_610_0.png)

![](img/5b3fa86b6571b68f1313de4e5d81fe8a_610_1.png)

## (2) XML Schema

- XML Schema is a more sophisticated schema language which addresses the drawbacks of DTDs. Supports
  - Typing of values
    - E.g. integer, string, etc
    - Also, constraints on min/max values
  - User-defined, complex types
  - Many more features, including
    - uniqueness and foreign key constraints, inheritance
- XML Schema is itself specified in XML syntax, unlike DTDs
  - More-standard representation, but verbose
- XML Scheme is integrated with namespaces
- BUT: XML Schema is significantly more complicated than DTDs.

## XML Schema Version of Bank DTD

```xml
<xs:schema xmlns:xs=http://www.w3.org/2001/XMLSchema>
<xs:element name="bank" type="BankType"/>
<xs:element name="account">
    <xsi:complexType>
        <xsi:sequence>
            <xsi:element name="account_number" type="xs:string"/>
            <xsi:element name="branch_name"    type="xs:string"/>
            <xsi:element name="balance"       type="xs:decimal"/>
        </xsi:sequence>
    </xsi:complexType>
</xs:element>
```

## XML Schema Version of Bank DTD

...definitions of customer and depositor...

```xml
<xs:complexType name="BankType">
  <xs:sequence>
    <xs:element ref="account" minOccurs="0"
                maxOccurs="unbounded"/>
    <xs:element ref="customer" minOccurs="0"
                maxOccurs="unbounded"/>
    <xs:element ref="depositor" minOccurs="0"
                maxOccurs="unbounded"/>
  </xs:sequence>
</xs:complexType>
</xs:schema>
```

