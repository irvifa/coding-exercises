# Univalue Tree

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
    public boolean solve(Tree root) {
        if (root == null) {
            return true;
        }

        return isSame(root.val, root);
    }

    private boolean isSame(int val, Tree root) {
        boolean current = (val == root.val);
        boolean right = (root.right == null)? true :isSame(val, root.right);
        boolean left = (root.left == null)? true : isSame(val, root.left);
        return  current && left && right;
    }
}
```
