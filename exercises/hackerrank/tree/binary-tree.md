# Binary Tree

```
import java.util.*;
import java.io.*;

class Node {
    Node left;
    Node right;
    int data;
    
    public Node(int data) {
        this.data = data;
        left = null;
        right = null;
    }
}

class Solution {
    public static int height(Node root) {
      if (root == null) {
          return -1;
      }
      return Math.max(height(root.left), height(root.right)) + 1;
    }
    public static Node insert(Node root, int data) {
        if(root == null) {
            return new Node(data);
        } else {
            Node cur;
            if(data <= root.data) {
                cur = insert(root.left, data);
                root.left = cur;
            } else {
                cur = insert(root.right, data);
                root.right = cur;
            }
            return root;
        }
    }
}
```
