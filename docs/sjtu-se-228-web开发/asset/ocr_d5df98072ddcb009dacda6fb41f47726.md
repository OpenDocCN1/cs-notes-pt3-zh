```
```java
@Entity
public class Person {
    @Id Integer getId() { ... }
    ...
}
```
```

```
```xml
<id
    name="propertyName"
    type="typename"
    column="column_name"
    unsaved-value="null|any|none|undefined|id_value"
    access="field|property|ClassName" >
    node="element-name|@attribute-name|element/@attribute|."
    <generator class="generatorClass"/>
</id>
```
```