# Binary Search

Anki ➡️ 05-binary-search

**Question 1**: *Find Minimum in Rotated Sorted Array*

Question can be found [here](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/description/)

**Solution**:

```python
class Solution:
    def findMin(self, nums: list[int]) -> int:
        l,r = 0 ,len(nums) - 1
        res = nums[0]

        while l<=r:
            if nums[l]<nums[r]:
                res = min(nums[l],res)
                break
            m = (l +r )//2
            res = min(nums[m],res)
            if nums[m]>= nums[l]:
                l = m + 1
            else:
                r = m - 1
        return res
```

Time : O(logn)

Space :O(1)

