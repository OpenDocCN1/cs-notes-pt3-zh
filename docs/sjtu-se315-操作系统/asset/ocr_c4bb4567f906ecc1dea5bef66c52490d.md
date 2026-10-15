# Why do developers ignore error handling?

+   Developers think the errors will never happen

+   Code evolution may enable the errors

+   The judgment can be wrong

```
} catch (IOException e) {
// will never happen
}
```

+   Error handling is difficult

+   Errors can be returned by 3rd party libraries

```
} catch (NoTransitionException e) {
/* Why this can happen? Ask God not me. */
}
```

+   Feature development is prioritized