# Merging Binary Tree

```
import java.util.*;

/**
 * public class Tree {
 *   int val;
 *   Tree left;
 *   Tree right;
 * }
 */
class Solution {
    public Tree solve(Tree a, Tree b) {
        if (b == null) {
            return a;
        }

        if (a == null) {
            return b;
        }
        
        a.val = b.val + a.val;
        a.left = solve(a.left, b.left);
        a.right = solve(a.right, b.right);
        return a;
    }
}

```
