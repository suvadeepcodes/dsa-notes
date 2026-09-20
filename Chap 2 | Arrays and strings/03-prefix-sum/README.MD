# Prefix Sum Theory

## Theory

- prefix[i] ➡️ sum of all elements up to index i

- Example 

  ```bash
  nums = [5,2,1,6,3,8]
  prefix = [5,7,8,14,17,25] 
  ```

- Sum of any subarray from i to j (inclusive) 

  -  `prefix[j] - prefix[i] + nums[i]` 
  - `prefix[j] - prefix[i-1]`
  -  Time and Space Complexity of calculating sum of subarray from i to j (inclusive)
     -  Time : O(1)
     -  Space : O(1) 

- Building a prefix sum ➡️

  ```js
  // Given an array nums 
  let prefix = [nums[0]]
  for(let i =1 ;i<nums.length ; i++){
  	prefix.push(nums[i] + prefix[i-1])
  }
  ```

  - Time and Space Complexity of building a prefix sum 
    - Time : O(n)
    - Space : O(n)
