# Min Steps to Make Piles Equal Height

```
/*
N piles of equal or unequal heights. In one step, we can remove any number of boxes from the pile which has the maximum height and try to make it equal to the one which is just lower than the maximum height of the stack. Determine the minimum number of steps required to make all of the piles equal in height.

Example 1:

Input: piles = [5, 2, 1]
Output: 3
Explanation:
Step 1: reducing 5 -> 2 [2, 2, 1]
Step 2: reducing 2 -> 1 [2, 1, 1]
Step 3: reducing 2 -> 1 [1, 1, 1]
So final number of steps required is 3.
*/

public int minSteps(int[] piles){
    int len = piles.length;
    if(len <= 1) return 0;
    Arrays.sort(piles);
    int res = 0, distinctNums = 0;
    for(int i = 1; i < len; ++i){
        if(piles[i] != piles[i - 1]){
            ++distinctNums;
        }
        res += distinctNums;
    }
    return res;
}
```
