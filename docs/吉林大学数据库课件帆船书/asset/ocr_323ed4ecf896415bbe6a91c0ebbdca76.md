# XML Schema Version of Univ. DTD (Cont.)

```
<xs:complexType name="UniversityType">
    <xs:sequence>
        <xs:element ref="department" minOccurs="0" maxOccurs="unbounded"/>
        <xs:element ref="course" minOccurs="0" maxOccurs="unbounded"/>
        <xs:element ref="instructor" minOccurs="0" maxOccurs="unbounded"/>
        <xs:element ref="teaches" minOccurs="0" maxOccurs="unbounded"/>
    </xs:sequence>
</xs:complexType>
</xs:schema>
```

+   - Choice of “xs:” was ours -- any other namespace prefix could be chosen
+   - Element “university” has type “universityType”, which is defined separately
+     - xs:complexType is used later to create the named complex type “UniversityType”