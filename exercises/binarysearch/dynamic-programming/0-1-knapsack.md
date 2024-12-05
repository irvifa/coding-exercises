# 0 - 1 Knapsack

```
import java.util.*;

class Solution {
    public int solve(int[] weights, int[] values, int capacity) {
        int n = values.length;
        int[][] K = new int[n + 1][capacity + 1];
        for(int i = 0; i <= n; i++) {
            for(int j = 0; j <= capacity; j++) {
                if (i == 0 || j == 0)
                    K[i][j] = 0;
                else if (weights[i - 1] <= j)
                    K[i][j] = Math.max(values[i - 1] +
                                    K[i - 1][j - weights[i - 1]],
                                    K[i - 1][j]);
                else
                    K[i][j] = K[i - 1][j];
            }
        }
        return K[n][capacity];
    }
}
```
