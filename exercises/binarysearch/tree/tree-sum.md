# Tree Sum

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
    public int solve(Tree root) {
        if (root == null) {
            return 0;
        }
        return root.val + solve(root.left) + solve(root.right);
    }
}
```
