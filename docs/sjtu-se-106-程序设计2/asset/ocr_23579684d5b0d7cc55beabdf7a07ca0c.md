# Efficiency of Selection Sort

+   - The primary question for today is how one might evaluate the efficiency of an algorithm such as selection sort.
+   - One strategy is to measure the actual time it takes to run for arrays of different sizes. In C++, you can measure elapsed time by calling the `time` function, which returns the current time in milliseconds. Using this strategy, however, requires some care:
+     - The `time` function is often too rough for accurate measurement. It therefore makes sense to measure several runs together and then divide the total time by the number of repetitions.
+     - Most algorithms show some variability depending on the data. To avoid distortion, you should run several independent trials with different data and average the results.
+     - Some measurements are likely to be wildly off because the computer needs to run some background task. Such data points must be discarded as you work through the analysis.