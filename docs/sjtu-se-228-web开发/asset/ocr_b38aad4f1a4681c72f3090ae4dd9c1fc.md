+   - Person.hbm.xml
+   ```xml
+   <class name="Person" table="PERSON">
+       <id name="id" column="PERSON_ID">
+           <generator class="native"/>
+       </id>
+       <property name="age"/>
+       <property name="firstname"/>
+       <property name="lastname"/>
+       <set name="events" table="PERSON_EVENT">
+           <key column="PERSON_ID"/>
+           <many-to-many column="EVENT_ID" class="Event"/>
+       </set>
+   </class>
+   ```
+   - Hibernate’s configuration
+   ```xml
+   <mapping resource="org/hibernate/tutorial/domain/Event.hbm.xml"/>
+   <mapping resource="org/hibernate/tutorial/domain/Person.hbm.xml"/>
+   ```