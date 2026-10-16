# # Identifying Bottlenecks

+   - Transactions request a sequence of services
+   
+     - E.g., CPU, Disk I/O, locks

With concurrent transactions, transactions may have to wait for a requested service while other transactions are being served

+   - Can model database as a queuing system with a queue for each service
+   
+     - Transactions repeatedly do the following
+   
+       - request a service, wait in queue for the service, and get serviced

+   - Bottlenecks in a database system typically show up as very high utilizations (and correspondingly, very long queues) of a particular service
+   
+     - E.g., disk vs. CPU utilization
+   
+     - 100% utilization leads to very long waiting time:
+   
+       - Rule of thumb: design system for about 70% utilization at peak load
+   
+       - utilization over 90% should be avoided