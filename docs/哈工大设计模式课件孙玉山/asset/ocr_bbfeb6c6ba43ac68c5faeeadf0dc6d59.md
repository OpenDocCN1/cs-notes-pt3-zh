# Example 2: tax computation problem (税收问题)

两个对象是怎样被链接在一起的呢？

```
TaxVisitor v = new TaxVisitor();
Tax tax = new ElectronicTax();
tax.accept(v)
```

tax.accept(v); 使用accept方法，而不是通过构造方法将访问者对象拉入

Client
main()

ElectronicTax
+accept(Visitor v)
+getData:double

v.visitElectronicTax(this)

tax.getData()

v. visitElectronicTax()

TaxVisitor
+visitElectronicTax (ElectronicTax e){
e.getData();
}

Interactions involved in the above design