# Maximum Subarray

```
class Solution {
    public int maxSubArray(int[] nums) {
        int currentSubarray = 0;
        int maxSubarray = Integer.MIN_VALUE;
        
        for (int num: nums) {
            currentSubarray = Math.max(num, currentSubarray + num);
            maxSubarray = Math.max(maxSubarray, currentSubarray);
        }
        
        return maxSubarray;
    }
}
```
