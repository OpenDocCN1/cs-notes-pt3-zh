# Optimizing Nested Subqueries (Cont.)

In general, SQL queries of the form below can be rewritten as shown

+   - Rewrite: **select ...**
+     **from** *L₁*
+     **where** *P₁* and exists (**select ***
+     **from** *L₂*
+     **where** *P₂*)

+   - To: **create table** *t₁* as
+     **select distinct** *V*
+     **from** *L₂*
+     **where** *P₂¹*
+   
+     **select ...**
+     **from** *L₁, t₁*
+     **where** *P₁* and *P₂²*

+   - *P₂¹* contains predicates in *P₂* that do not involve any correlation variables

+   - *P₂²* reintroduces predicates involving correlation variables, with relations renamed appropriately

+   - V contains all attributes used in predicates with correlation variables