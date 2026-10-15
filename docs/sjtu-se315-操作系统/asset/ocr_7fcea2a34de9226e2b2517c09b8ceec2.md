# Example

| Programs | locks_held(t) | C(v) |
|---|---|---|
| lock(mu1); | { } | {mu1, mu2} |
| lock(mu2); | {mu1} | |
| v = v + 1; | {mu1, mu2} | {mu1, mu2} |
| unlock(mu2); | | |
| v = v + 2; | {mu1} | {mu1} |
| unlock(mu1); | | |
| lock(mu2); | { } | |
| v = v + 1; | {mu2} | { } Warning!! |
| unlock(mu2); | | |