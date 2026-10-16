# Lock Table

![](bbox=[0.08, 0.22, 0.48, 0.85])

+   - Dark blue rectangles indicate granted locks; light blue indicate waiting requests
+   - Lock table also records the type of lock granted or requested
+   - New request is added to the end of the queue of requests for the data item, and granted if it is compatible with all earlier locks
+   - Unlock requests result in the request being deleted, and later requests are checked to see if they can now be granted
+   - If transaction aborts, all waiting or granted requests of the transaction are deleted
+     - lock manager may keep a list of locks held by each transaction, to implement this efficiently