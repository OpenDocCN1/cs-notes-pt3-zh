# 15.5 Optimal binary search trees

+   - Need the total time spent searching to be as low as possible.
+   - Words appear with different frequencies.
+   - It may be: “algorithm” (frequently used) appears far from the root; “mycophagist” (rarely used, 食菌者) appears near the root.
+   （高频出现的单词出现在远离树根的节点，......）
+   - Such an organization would slow down the translation, since # of nodes visited when searching for a key in a BST is “one plus the depth of the node containing the key” (1+depth).
+   - We want words that occur frequently in the text to be placed nearer the root.

![](bbox=[0.65, 0.04, 0.97, 0.62])