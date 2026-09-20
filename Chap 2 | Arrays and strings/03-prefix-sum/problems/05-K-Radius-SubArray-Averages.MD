# 2040. K Radius SubArray Averages

Question can be found [here](https://leetcode.com/problems/k-radius-subarray-averages/)

**Solution**:

```js

var getAverages = function(nums, k) {
    // When a single element is considered then its average will be the number itself only.
    if (k === 0) {
        return nums;
    }
    
    const windowSize = 2 * k + 1
    const n = nums.length;
    const averages = new Array(n).fill(-1);

    // Any index will not have 'k' elements in its left and right.
    if (windowSize > n) {
        return averages;
    }

    
    prefix =[nums[0]];
    for(let i=1;i<nums.length;i++){
        prefix.push(nums[i]+prefix[prefix.length-1])
    }
    
    // We iterate only on those indices which have at least 'k' elements in their left and right.
    // i.e. indices from 'k' to 'n - k'
    for (let i = k; i < (n - k); i++) {
        const leftBound = i - k,
        const rightBound = i + k;
        const subArraySum = prefix[rightBound ] - prefix[leftBound] + nums[leftBound];
        const average = Math.floor(subArraySum / windowSize);
        averages[i] = average;
    }

    return averages;
};
```

- Time and Space Complexity : 
  - Time : 
  - Space : 