# # Disk Access Time Example

# ## Given:

+   - Rotational rate = 7,200 RPM
+   - Average seek time = 9 ms.
+   - Avg # sectors/track = 400.

# ## Derived:

+   - \( T_{\text{avg rotation}} = \)
+   - \( T_{\text{avg transfer}} = \)
+   - \( T_{\text{access}} = \)

+   - **Average time to access some target sector approximated by:**
+     - \( T_{\text{access}} = T_{\text{avg seek}} + T_{\text{avg rotation}} + T_{\text{avg transfer}} \)
+   - **Seek time (**\( T_{\text{avg seek}} \)**)**
+     - Time to position heads over cylinder containing target sector.
+     - Typical \( T_{\text{avg seek}} \) is 3–9 ms
+   - **Rotational latency (**\( T_{\text{avg rotation}} \)**)**
+     - Time waiting for first bit of target sector to pass under r/w head.
+     - \( T_{\text{avg rotation}} = 1/2 \times 1/\text{RPMs} \times 60 \text{ sec}/1 \text{ min} \)
+     - Typical \( T_{\text{avg rotation}} = 7,200 \text{ RPMs} \)
+   - **Transfer time (**\( T_{\text{avg transfer}} \)**)**
+     - Time to read the bits in the target sector.
+     - \( T_{\text{avg transfer}} = 1/\text{RPM} \times 1/(\text{avg # sectors/track}) \times 60 \text{ secs}/1 \text{ min} \).