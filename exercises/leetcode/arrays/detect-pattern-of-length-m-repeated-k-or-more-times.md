# Detect Pattern of Length M Repeated K or More Times

### Description

[https://leetcode.com/problems/detect-pattern-of-length-m-repeated-k-or-more-times/](https://leetcode.com/problems/detect-pattern-of-length-m-repeated-k-or-more-times/)

### Implementation

**Sliding Window Technique**

* Iterate through possible starting positions
* Check if a pattern of length `m` repeats `k` times consecutively
* Time Complexity: O(n \* m \* k)&#x20;
* Space Complexity: O(1)

### C++

```
#include <vector>
#include <algorithm>
#include <functional>
#include <ranges>

class PatternValidator {
public:
    bool validate(const std::vector<int>& arr, int start, int m, int k) {
        for (int repeat = 1; repeat < k; ++repeat) {
            int patternOffset = start + repeat * m;
            
            if (!comparePatternSegments(arr, start, patternOffset, m)) {
                return false;
            }
        }
        return true;
    }

private:
    bool comparePatternSegments(const std::vector<int>& arr, 
                                int firstSegment, 
                                int secondSegment, 
                                int m) {
        return std::equal(
            arr.begin() + firstSegment, 
            arr.begin() + firstSegment + m,
            arr.begin() + secondSegment
        );
    }
};

class PatternMatcher {
public:
    static bool containsPattern(const std::vector<int>& arr, int m, int k) {
        if (arr.size() < m * k) return false;

        return std::ranges::any_of(
            std::views::iota(0, static_cast<int>(arr.size() - m * k + 1)),
            [&](int start) { 
                return checkPatternAtIndex(arr, start, m, k); 
            }
        );
    }

private:
    static bool checkPatternAtIndex(
        const std::vector<int>& arr,
        int start,
        int m,
        int k) {
        PatternValidator validator;
        return validator.validate(arr, start, m, k);
    }
};


class Solution {
public:
    bool containsPattern(vector<int>& arr, int m, int k) {
        return PatternMatcher::containsPattern(arr, m, k);
    }
};
```
