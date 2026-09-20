# 1413.Minimum Value to Get Positive Step by Step Sum

Question can be found [here](https://leetcode.com/problems/minimum-value-to-get-positive-step-by-step-sum/description/)

**Solution**:

```js
var minStartValue = function(nums) {
   let minVal =0;
    let total =0;
    for(let i=0;i<nums.length;i++){
        total+=nums[i];
        minVal =Math.min(minVal,total)
    }
    return 1-minVal
};
```

- Time and Space Complexity 
  - Time: 
  - Space: 

