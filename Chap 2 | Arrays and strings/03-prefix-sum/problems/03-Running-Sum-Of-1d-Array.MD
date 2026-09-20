# 1480.Running Sum of 1d Array

Question can be found [here](https://leetcode.com/problems/running-sum-of-1d-array/)

**Solution**:

```js
var runningSum = function(nums) {
let prefix =[nums[0]];
    for(let i=1;i<nums.length;i++){
        prefix.push(nums[i]+prefix[prefix.length-1])
    }
    return prefix;
};
```

- Time and Space Complexity
  - Time : 
  - Space : 