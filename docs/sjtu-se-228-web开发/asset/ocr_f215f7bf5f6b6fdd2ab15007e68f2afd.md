+   - The `struts.xml` File
+     - This configuration file contains the configuration information that you will be modifying as actions are developed.

```
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE struts PUBLIC
  "-//Apache Software Foundation
  //DTD Struts Configuration 2.0//EN"
  "http://struts.apache.org/dtds/struts-2.0.dtd">

<struts>
  <constant name="struts.devMode" value="true" />
  <package name="basicstruts2" extends="struts-default">
    <action name="index">
      <result>/index.jsp</result>
    </action>
    ....
  </package>
</struts>
```