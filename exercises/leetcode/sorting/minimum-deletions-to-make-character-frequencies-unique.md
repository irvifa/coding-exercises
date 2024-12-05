# Minimum Deletions to Make Character Frequencies Unique

```
class Solution {
    // time complexity O(N)
    public int minDeletions(String s) {
        final int SIZE = 26;
        int[] frequency = new int[SIZE];
        
        for (char c: s.toCharArray()) {
            frequency[c - 'a']++;
        }
        
        Arrays.sort(frequency);
        int minDelete = 0;
        int maxAllowed = s.length();
        
        for (int i = SIZE - 1; i >= 0 && frequency[i] > 0; i--) {
            if (frequency[i] > maxAllowed) {
                minDelete += frequency[i] - maxAllowed;
                frequency[i] = maxAllowed;
            }
            maxAllowed = Math.max(0, frequency[i] - 1);
        }
        return minDelete;
    }
}
```
