# # Embedded SQL (Cont.)

Step2: The open statement causes the query to be evaluated:

EXEC SQL OPEN c END_EXEC

Step3: The fetch statement causes the values of one tuple in the result of query to be placed on host language variables.

EXEC SQL FETCH c INTO :cn, :ccity END_EXEC

Repeated calls to fetch of successive tuples in the query result.

A variable called SQLSTATE in the SQLCA (SQL communication area) gets set to ‘02000’ to indicate no more data is available