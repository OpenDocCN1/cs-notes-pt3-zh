# Another Example-account management

设计优点：🙂

客户类的责任减少了。具体的对类库的调用责任交给了门面类CustomerFacade

+   - The CustomerFacade handles the details of
+     - creating necessary Subsystem objects and
+     - calling appropriate methods on those objects
+     to validate and save the customer data.
+   - The UserGUI is no longer required to directly access any of the subsystem (Account, Address, And CreditCard) objects.