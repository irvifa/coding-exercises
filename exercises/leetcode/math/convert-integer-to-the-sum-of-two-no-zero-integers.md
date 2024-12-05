# Convert Integer to the Sum of Two No-Zero Integers

### Description

Given an integer `n`, find two positive integers `a` and `b` such that:

* Neither `a` nor `b` contains the digit zero
* `a + b = n`

[Description](https://leetcode.com/problems/convert-integer-to-the-sum-of-two-no-zero-integers/description/)

### Approach

* Iterates through possible values of `a` from 1 to `n-1`
* Calculates `b` as `n - a`
* Check both `a` and `b`
* Returns the first valid pair found

### Implementation

#### Java

```
class Solution {
    private boolean hasNoZero(int num) {
        return !String.valueOf(num)
            .chars()
            .mapToObj(ch -> (char)ch)
            .anyMatch(ch -> ch == '0');
    }
    
    public int[] getNoZeroIntegers(int n) {
        return java.util.stream.IntStream
            .rangeClosed(1, n-1)
            .filter(a -> {
                int b = n - a;
                return hasNoZero(a) && hasNoZero(b);
            })
            .mapToObj(a -> new int[]{a, n-a})
            .findFirst()
            .orElse(new int[]{});
    }
}
```

#### C++

```
class Solution {
public:
    bool hasNoZero(int num) {
        string numStr = to_string(num);
        return numStr.find('0') == string::npos;
    }
    
    vector<int> getNoZeroIntegers(int n) {
        for (int a = 1; a < n; ++a) {
            int b = n - a;
            
            if (hasNoZero(a) && hasNoZero(b)) {
                return {a, b};
            }
        }
        
        return {};
    }
};
```

#### Rust

```
impl Solution {
    fn has_no_zero(num: i32) -> bool {
        num.to_string()
            .chars()
            .all(|c| c != '0')
    }
    
    pub fn get_no_zero_integers(n: i32) -> Vec<i32> {
        (1..n)
            .find_map(|a| {
                let b = n - a;
                if Self::has_no_zero(a) && Self::has_no_zero(b) {
                    Some(vec![a, b])
                } else {
                    None
                }
            })
            .unwrap_or_else(|| vec![])
    }
}
```

#### Go

```
func hasNoZero(num int) bool {
    return !strings.Contains(strconv.Itoa(num), "0")
}

func getNoZeroIntegers(n int) []int {
    for a := 1; a < n; a++ {
        b := n - a
        if hasNoZero(a) && hasNoZero(b) {
            return []int{a, b}
        }
    }
    return []int{}
}
```

### Complexity

* Time Complexity: O(n)
* Space Complexity: O(1)
