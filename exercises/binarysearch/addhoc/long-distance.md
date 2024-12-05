# Long Distance

```
class Solution:
    import bisect
    def solve(self, nums):
        res, inc = [], []
        while nums:
            num = nums.pop()
            res.append(bisect.bisect_left(inc, num))
            bisect.insort(inc, num)
        return res[::-1]
```
