# 303.Range Sum SubQuery - Immutable

Question can be found [here](https://leetcode.com/problems/range-sum-query-immutable/description/)

**Solution**:

```js

var NumArray = function(nums) {
    
    this.prefix = [nums[0]];
    for (let i = 1; i < nums.length; i++) {
        this.prefix[i] = this.prefix[i - 1] + nums[i];
    }
};

NumArray.prototype.sumRange = function(left, right) {
    if (left === 0) return this.prefix[right];
    return this.prefix[right] - this.prefix[left - 1];
};

```

Time and Space Complexity : 

- Time : 
- Space : 