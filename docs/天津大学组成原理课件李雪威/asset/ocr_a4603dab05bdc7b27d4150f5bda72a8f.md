# # Reassociated Computation

```
`x = x OP (d[i] OP d[i+1]);`
```

# ## What changed:

+   - Ops in the next iteration can be started early (no dependency)

# ## Overall Performance

+   - N elements, D cycles latency/op
+   - (N/2+1)*D cycles: CPE = D/2

![](bbox=[0.112, 0.357, 0.422, 0.837])