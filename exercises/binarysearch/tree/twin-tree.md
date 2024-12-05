# Twin Tree

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
    public boolean solve(Tree a, Tree b) {
        if (a == null && b == null) {
            return true;
        }
        if ((a == null && b != null) || (b == null && a != null)) {
            return false;
        }

        return a.val == b.val && solve(a.left, b.left) && solve(a.right, b.right);
    }
}
```
