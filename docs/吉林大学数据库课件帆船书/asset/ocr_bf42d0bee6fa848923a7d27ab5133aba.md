# Hardware Tuning: One-Minute Rule

+   - For sequentially accessed data, more pages can be read per second. Assuming sequential reads of 1MB of data at a time:
+     **1-minute rule: sequentially accessed data that is accessed once or more in a minute should be kept in memory**
+   - Prices of disk and memory have changed greatly over the years, but the ratios have not changed much
+     - So rules remain as 5 minute and 1 minute rules, not 1 hour or 1 second rules!