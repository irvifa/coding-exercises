# Contains Duplicate

```
class Solution {
    // Time complexity O(N)
    public boolean containsDuplicate(int[] nums) {
        Set<Integer> numbers = new HashSet<>();
        for (int n: nums) {
            if (numbers.contains(n)) {
                return true;
            }
            numbers.add(n);
        }
        return false;
    }
}
```
