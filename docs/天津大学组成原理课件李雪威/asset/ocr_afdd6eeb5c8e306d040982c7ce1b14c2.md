# # Byte Ordering Revisited

# ## Idea

+   - Short/long/quad words stored in memory as 2/4/8 consecutive bytes
+   - Which byte is most (least) significant?
+   - Can cause problems when exchanging binary data between machines

# ## Big Endian

+   - Most significant byte has lowest address
+   - Sparc, *Internet*

# ## Little Endian

+   - Least significant byte has lowest address
+   - Intel x86, ARM Android and IOS

# ## Bi Endian

+   - Can be configured either way
+   - ARM