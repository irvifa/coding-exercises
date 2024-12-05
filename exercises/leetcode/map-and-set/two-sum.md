# Two Sum

```
class Solution {
    // Time complexity: O(N)
    // Space complexity: O(N)
    public int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> map = new HashMap<>();
        
        for (int i = 0; i < nums.length; i++) {
            int n = nums[i];
            map.put(n, i);
        }
        
        for (int i = 0; i < nums.length; i++) {
            int complement = target - nums[i];
            if (map.containsKey(complement)) {
                int complementIndex = map.get(complement);
                if (complementIndex != i)
                    return new int[] {i, map.get(complement)};
            }
        }
        return null;
    }
}
```
