# Materialized View Selection

+   - **Materialized view selection**: “What is the best set of views to materialize?”.
+   - **Index selection**: “what is the best set of indices to create”
+     - closely related, to materialized view selection
+       - but simpler
+   - Materialized view selection and index selection based on typical system **workload** (queries and updates)
+     - Typical goal: minimize time to execute workload , subject to constraints on space and time taken for some critical queries/updates
+     - One of the steps in database tuning
+       - more on tuning in later chapters
+   - Commercial database systems provide tools (called “tuning assistants” or “wizards”) to help the database administrator choose what indices and materialized views to create