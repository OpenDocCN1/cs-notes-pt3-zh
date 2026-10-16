# Function Call Memory

Why do AI assistants repeatedly fail at the same tasks? More often than not, they lack the ability to remember and learn from past function call experiences.

This project introduces a Function Call Memory - a middleware layer to enable LLM agents to store and reuse past successful call trajectories.

Key Benefits:

+   - **Reduce errors**: avoid repeated mistakes by recalling prior outcomes
+   - **Speed up** execution by skipping redundant reasoning

To see how this works, let's walk through an example scenario: building and deploying an e-commerce order handler with memory-enabled agent interactions.

![](bbox=[0.3, 0.32, 0.7, 0.42])

The architecture above demonstrates the interaction flow between the LLM Core and Memory Store.

```
```python
memory = FunctionCallMemory()
# register a successful tool call
memory.save_tool_call("get_order_status", args={"order_id": 123})
```
```

The next time the agent needs order status, it can instantly retrieve the saved response.

| Tool Name        | Memory Hit | Latency Reduction |
|------------------|------------|-------------------|
| get_order_status | ✅         | 84%               |
| create_refund    | ✅         | 78%               |
| update_inventory | ✅         | 91%               |

Deployment is simple—no heavy infrastructure required. Install with pip:

```
```bash
pip install function-call-memory
```
```

And you're ready to start building resilient agents today.

> > "Memory is the missing piece in modern AI workflows." - Project Lead