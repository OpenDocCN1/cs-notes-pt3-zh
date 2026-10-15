# Push in Action

+   - Let us Assume T1 Succeeds, therefore T1 exits out of the while and consequently the push()

```
do {
    node->next = head;
} while (!cas(&head, node, node->next));
```

+   - T2’s cas failed why? Hint: Look at the picture.

+   - T2 has no choice but to try again