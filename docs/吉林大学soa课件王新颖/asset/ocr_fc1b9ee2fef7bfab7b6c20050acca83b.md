```
<mappings xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://xfire.codehaus.org/schemas/1.0/mapping.xsd">
<mapping>
    <method name="test">
        <parameter index="0" mappedName="userId"/>
        <return-type mappedName="Long" />
    </method>
    <method name="person_search">
        <parameter index="0" mappedName="keyword"/>
        <return-type mappedName="PersonList" componentType="edu.thu.keg.core.model.indexer.PersonSearchResult"/>
    </method>
</mapping>
</mappings>
```