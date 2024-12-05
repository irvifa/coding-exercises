# Minimum Sum of Four Digit Number After Splitting Digits

```
class Solution {
    // O(N log N) where N is always 4
    public int minimumSum(int num) {
        List<Integer> arr = new ArrayList<>();
        while (num > 0) {
            int n = num%10;
            arr.add(n);
            num /= 10;
        }
        Collections.sort(arr);
        int x = arr.get(0)*10 + arr.get(3);
        int y = arr.get(1)*10 + arr.get(2);
        return x + y;
    }
}
```
