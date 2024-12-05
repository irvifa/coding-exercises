# Mutual Followers

```
import java.util.*;

class Solution {
    public int[] solve(int[][] relations) {
        Set<Pair<Integer, Integer>> g = new HashSet<>();
        for (int[] relation: relations) {
            g.add(new Pair(relation[0], relation[1]));
        }

        Set<Integer> s = new HashSet<>();
        for (Pair<Integer, Integer> edge: g) {
            int other = edge.getValue();
            int person = edge.getKey();
            if (g.contains(new Pair(other, person))) {
                s.add(person);
                s.add(person);
            }
        }

        int[] ret = new int[s.size()];
        int i = 0;
        for (int n: s) {
            ret[i] = n;
            i++;
        }
        Arrays.sort(ret);
        return ret;
    }
}
```
