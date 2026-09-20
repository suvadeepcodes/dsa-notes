# 724.Find Pivot Index

Question can be found [here](https://leetcode.com/problems/find-pivot-index/description/)

**Solution**:

```js
var pivotIndex = function(nums) {
    let prefix = [nums[0]];

    for (let i = 1; i < nums.length; i++) {
        prefix.push(nums[i] + prefix[i - 1]);
    }

    for (let i = 0; i < nums.length; i++) {
        let left = i === 0 ? 0 : prefix[i - 1];
        let right = prefix[nums.length - 1] - prefix[i];

        if (left === right) return i;
    }

    return -1;
};
```

- Time and Space Complexity 
  - Time : 
  - Space : 