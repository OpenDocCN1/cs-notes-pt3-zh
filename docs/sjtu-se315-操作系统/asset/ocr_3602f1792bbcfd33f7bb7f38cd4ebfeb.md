# Terms for properties of fs ops

What effects will app see after restart + recovery
creat("a"); fd = creat("b"); write(fd,...); crash

Durable: effects of operation are visible
Both a and b are visible

Atomic: all steps of operation visible or none
Either a and b are visible or none is visible

Ordered: exactly a prefix of operations is visible
If b is visible, then a is visible