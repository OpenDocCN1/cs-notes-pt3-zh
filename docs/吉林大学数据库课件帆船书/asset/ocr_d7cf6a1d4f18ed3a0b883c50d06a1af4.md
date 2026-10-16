![](bbox=[0.0, 0.03, 0.07, 0.15])

# ARIES Optimizations

+   - **Physiological redo**
+     - Affected page is physically identified, action within page can be logical
+       - Used to reduce logging overheads
+         - e.g. when a record is deleted and all other records have to be moved to fill hole
+           - Physiological redo can log just the record deletion
+           - Physical redo would require logging of old and new values for much of the page
+       - Requires page to be output to disk atomically
+         - Easy to achieve with hardware RAID, also supported by some disk systems
+         - Incomplete page output can be detected by checksum techniques,
+           - But extra actions are required for recovery
+           - Treated as a media failure