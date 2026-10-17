# ## 2.8 Communicating with People Beyond Numbers

+   ASCII ( American Standard Code for Information Interchange )

+   Instructions for moving bytes in MIPS

+   Load byte ( lb ): lb $t0, 0($sp) # read byte from source

+   Store byte ( sb ): sb $t0, 0($sp) # write byte to destination

+   Three choices for representing a string

+   Place the length of the string in the first position

+   An accompanying variable has the length

+   A character in the last position to mark the end of a string

+   C uses the third choice

+   Terminate a string with a byte whose value is 0 ( null in ASCII )