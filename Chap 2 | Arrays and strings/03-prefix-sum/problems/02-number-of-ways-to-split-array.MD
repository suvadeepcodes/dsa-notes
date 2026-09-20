# Number of ways to split array 

Question can be found [here](https://leetcode.com/problems/number-of-ways-to-split-array/description/)

**Solution**:

```js
var waysToSplitArray = function(nums) {
    let prefix = [nums[0]];

    for(let i=1;i<nums.length;i++){
        prefix.push(nums[i] + prefix[i-1])
    }

    let ans = 0 ;
    for(let i=0;i<nums.length-1;i++){
        let leftSide = prefix[i] 
        let rightSide = prefix[nums.length - 1] - prefix[i+1] + nums[i+1];

        if(leftSide >= rightSide) ans++
    }

    return ans;
};
```

Time and Space Complexity : 

- Time : 
- Space : 