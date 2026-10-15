# Results / View Technologies

+   - There are three other technologies that can replace JSPs in a Struts2 application:
+     - Velocity Templates
+     - Freemarker Templates
+     - XSLT Transformations

```
<action name="my" class="com.fdar.infoq.MyAction">
    <result type="freemarker">view.ftl</result>
</action>
```

```
<result type="xslt">
    <param name="stylesheetLocation">render.xslt</param>
    <param name="exposedValue">model.address</param>
</result>
```