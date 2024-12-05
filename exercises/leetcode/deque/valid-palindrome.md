# Valid Palindrome

```
/*
Input: s = "A man, a plan, a canal: Panama"
Output: true
Explanation: "amanaplanacanalpanama" is a palindrome.

Input: s = "race a car"
Output: false
Explanation: "raceacar" is not a palindrome.
*/
class Solution {
    // Time complexity: O(N)
    public boolean isPalindrome(String s) {
        Deque<Character> deque = new ArrayDeque<>();
        s = s.toLowerCase();
        for (char c: s.toCharArray()) {
            if (isDigitOrCharacter(c)) {
                deque.offer(c);
            }
        }
        while (deque.size() >= 2) {
            int first = deque.pollFirst();
            int last = deque.pollLast();
            if (first != last) {
                return false;
            }
        }
        return deque.size() <= 1;
    }
    
    private boolean isDigitOrCharacter(char c) {
        return (c >= 'a' && c <= 'z') || (c >= '0' && c <= '9');
    }
}
```
