# Addhoc

```
import java.util.*;

class Solution {
    /**
    I keep the number of flips that I have done.
If the number of flips is even, it means that the current number is maintained. If not, it's flipped.
If I have 0 and even flips, I'm ok. If I have 1 and odd flips, I'm also ok because that 1 was already flipped. Otherwise I need to do one more flip.

This solution is \mathcal{O}(n)O(n) where nn is the length of the sequence.

    */
    public int solve(int[] nums) {
        int flips = 0;
        for (int n: nums) {
            if (flips % 2 == n) {
                continue;
            } else {
                flips++;
            }
        }
        return flips;
    }
}
```
