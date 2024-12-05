---
description: >-
  Given two nodes of a binary tree, return their Lowest Common Ancestor (LCA).
  LCA is a node within a tree T is the lowest node that has both p and q as
  descendants.
---

# Lowest Common Ancestor (LCA)

```
class Node {
    public int val;
    public Node left;
    public Node right;
    public Node parent;
};
```

```
public Node lowestCommonAncestor(Node p, Node q) {
    Node a = p;
    Node b = q;
    while(a != b) {
        a = a == null ? q : a.parent;
        b = b == null ? p : b.parent;  
    }
    return a;
}
```
