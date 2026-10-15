# DML: Query

+   • join-expression :
+   table-expr. join-operator table-expr. [ ON join-condition ]

+   – join-operator :
+   [ KEY | NATURAL ] [ join-type ] JOIN | CROSS JOIN

+   • join-type :
+   INNER
+   | LEFT [ OUTER ]
+   | RIGHT [ OUTER ]
+   | FULL [ OUTER ]