# Exercise: Preorder Traversal

![](bbox=[0.18, 0.22, 0.88, 0.45])

```
void preorderTraversal(Node *t) {
    if (t != null) {
        cout << t->key << endl;
        preorderTraversal(t->left);
        preorderTraversal(t->right);
    }
}
```

![](bbox=[0.58, 0.52, 0.88, 0.73])