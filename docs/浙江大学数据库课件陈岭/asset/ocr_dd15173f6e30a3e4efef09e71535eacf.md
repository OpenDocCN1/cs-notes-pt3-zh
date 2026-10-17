# XML Schema Version of Bank DTD

```
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
```