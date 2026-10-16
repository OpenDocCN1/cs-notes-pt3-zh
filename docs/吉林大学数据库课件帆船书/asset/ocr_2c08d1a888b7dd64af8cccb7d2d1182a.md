# # Measuring Retrieval Effectiveness

+   - Information-retrieval systems save space by using index structures that support only approximate retrieval. May result in:
+     - **false negative (false drop)** - some relevant documents may not be retrieved.
+     - **false positive** - some irrelevant documents may be retrieved.
+     - For many applications a good index should not permit any false drops, but may permit a few false positives.

+   - Relevant performance metrics:
+     - **precision** - what percentage of the retrieved documents are relevant to the query.
+     - **recall** - what percentage of the documents relevant to the query were retrieved.