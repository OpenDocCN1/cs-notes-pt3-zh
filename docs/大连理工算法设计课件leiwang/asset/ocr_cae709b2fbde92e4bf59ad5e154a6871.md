# # Running time

On a particular input, **_the running time_** is the number of primitive operations (steps) executed.

+   - Want to define steps to be machine-independent.
+   - Each line of pseudocode requires a constant amount of time.
+   - One line may take a different amount of time than another, but each execution of line _i_ takes the same amount of time _c<sub>i</sub>_.
+   - This is assuming that the line consists only of primitive operations.

The running time of an algorithm is:

\(\sum_{\text{all statements}} \text{(cost of statement)} \times \text{(# of times statement is executed)}\)