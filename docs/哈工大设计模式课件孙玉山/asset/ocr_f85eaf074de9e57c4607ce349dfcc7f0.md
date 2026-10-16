# Case study 1. Legacy File Update

# Some issues about a pipe

+   a) **Amount of data in a pipe**: Pipe objects limit the amount of data they can hold.

+   b) **Data consumption**. However, whenever clients read the data from a pipe, this data is considered "consumed" and the space that was occupied by the retrieved data is made free again.