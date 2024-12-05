# Tree Traversal

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
    public int solve(Tree root, String[] moves) {
        var stack = new Stack<Tree>();
        for (var move : moves) {
            switch (move) {
                case "RIGHT":
                    stack.push(root);
                    root = root.right;
                    break;
                case "LEFT":
                    stack.push(root);
                    root = root.left;
                    break;
                case "UP":
                    root = stack.pop();
            }
        }
        return root.val;
    }
}
```
