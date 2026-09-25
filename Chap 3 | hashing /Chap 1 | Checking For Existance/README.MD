# Chap 1 | Checking For Existence

| Problem                               | Status |
| ------------------------------------- | ------ |
| 1. Two Sum                            |        |
| 2351. First Letter to appear twice    |        |
| Find Isolated Number                  |        |
| 1832.Check if the sentence is anagram |        |
| 268.Missing Number                    |        |
| 1426.Counting Elements                |        |
| 217.Contains Duplicate                |        |
| 1436.Destination City                 |        |
| 1496. Path Crossing                   |        |

---

## Theory

- One of the most common applications of a hash map or set is determining if an element exists in O(1)*O*(1)

---

## Problems

1. Two Sum 

Question can be found [here](https://leetcode.com/problems/two-sum/description/)

**Solution**:

```js
var twoSum = function(nums, target) {

  const myMap = new Map();

  for (let i = 0; i < nums.length; i++) {

    const complement = target - nums[i];

    if (myMap.has(complement)) {
      return [myMap.get(complement), i];
    }

    myMap.set(nums[i], i);
  }
};
```

Time and Space Complexity : 

- Time : O(n)
- Space :O(n)

---

2351.First Letter to Appear Twice 

Question can be found [here](https://leetcode.com/problems/first-letter-to-appear-twice/description/)

**Solution**:

```js
var repeatedCharacter = function(s) {
    let seen = new Set();
    for (const c of s) {
        if (seen.has(c)) {
            return c;
        }
        
        seen.add(c);
    }
    
    return " ";
};
```

---

Find Isolated Number 

Given an integer array `nums`, find all the numbers `x` in `nums` that satisfy the following: `x + 1` is not in `nums`, and `x - 1` is not in `nums`.

If a valid number `x` appears multiple times, you only need to include it in the answer once.

```js
let findNumbers = nums => {
    
}
```

**Solution**:

```js
let findNumbers = nums => {
    let ans = [];
    let numsSet = new Set(nums);

    for (const num of numsSet) {
        if (!numsSet.has(num + 1) && !numsSet.has(num - 1)) {
            ans.push(num);
        }
    }

    return ans;
}
```

---

1832.Check if the sentence is Panagram 

Question can be found [here](https://leetcode.com/problems/check-if-the-sentence-is-pangram/description/)

