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

  ```python
  prefix = [nums[0]]
  
  for i in range(1, len(nums)):
      prefix.append(nums[i] + prefix[i - 1])
  ```
  
  - Time and Space Complexity of building a prefix sum 
    - Time : O(n)
    - Space : O(n)

---

## Problems 

### Q1 : Range Sum SumQueries

Given an integer array `nums`, an array `queries` where `queries[i] = [x, y]` and an integer `limit`, return a boolean array that represents the answer to each query. A query is `true` if the sum of the subarray from `x` to `y` is less than `limit`, or `false` otherwise.

For example, given `nums = [1, 6, 3, 2, 7, 2]`, `queries = [[0, 3], [2, 5], [2, 4]]`, and `limit = 13`, the answer is `[true, false, true]`. For each query, the subarray sums are `[12, 14, 12]`.

```python
def answerQueries(nums, queries, limit):
```

**Solution**:

```js
def answerQueries(nums, queries, limit):
    prefix = [nums[0]]

    for i in range(1, len(nums)):
        prefix.append(nums[i] + prefix[i - 1])

    ans = []

    for x, y in queries:
        curr = prefix[y] - prefix[x] + nums[x]
        ans.append(curr < limit)

    return ans


nums2 = [1, 6, 3, 2, 7, 2]
queries2 = [[0, 3], [2, 5], [2, 4]]
limit2 = 13

print(answerQueries(nums2, queries2, limit2))
```

**Complexity** ➡️ 

- **Time: `O(n + q)`**
   We traverse `nums` once to build the prefix sum array → `O(n)`, then process each query once → `O(q)`. Each query takes **O(1)** time.
- **Space: `O(n + q)`**
   The `prefix` array stores `n` elements → `O(n)`, and the `ans` array stores `q` results → `O(q)`.

**Where:** `n = nums.length`, `q = queries.length`.

---

**Q2** 2270.Number of ways to split array 

Question can be found [here](https://leetcode.com/problems/number-of-ways-to-split-array/description/)

**Solution**:

```js
def waysToSplitArray(nums):
    prefix = [nums[0]]

    for i in range(1, len(nums)):
        prefix.append(nums[i] + prefix[i - 1])

    ans = 0

    for i in range(len(nums) - 1):
        left = prefix[i]
        right = prefix[len(nums) - 1] - prefix[i]

        if left >= right:
            ans += 1

    return ans
```

**Note: Valid Split Range**

When splitting an array into **two non-empty subarrays**, the split can only happen between index `0` and `n - 2`.

```js
for i in range(len(nums) - 1):
```

Do **not** check `i = nums.length - 1`, because that would make the right subarray empty.

**Remember:** For `n` elements, there are exactly **`n - 1` possible split points**.

### Time & Space Complexity

- **Time Complexity: `O(n)`** — We traverse the array once to build the prefix sum and once to check all valid splits. `O(n) + O(n) = O(n)`.
- **Space Complexity: `O(n)`** — We create a `prefix` array containing `n` elements.

---

**Q3**: 1480.Running Sum of 1d Array

Question can be found [here](https://leetcode.com/problems/running-sum-of-1d-array/)

**Solution**:

```js
def runningSum(nums):
    prefix = [nums[0]]

    for i in range(1, len(nums)):
        prefix.append(nums[i] + prefix[i - 1])

    return prefix
```

### Time & Space Complexity

- **Time Complexity: `O(n)`** — We iterate through the array once.
- **Space Complexity: `O(n)`** — We create a new `prefix` array containing `n` elements.

---

**Q4**: 1413.Minimum Value to Get Positive Step by Step Sum

Question can be found [here](https://leetcode.com/problems/minimum-value-to-get-positive-step-by-step-sum/description/)

**Solution**:

```python
def minStartValue(nums):
    minVal = 0
    total = 0

    for i in range(len(nums)):
        total += nums[i]
        minVal = min(minVal, total)

    return 1 - minVal
```

Note ➡️

We track the **minimum prefix sum** because the starting value must be large enough to keep every running total at least `1`. So : `return 1 - minVal;` gives the **smallest starting value** that prevents the running sum from dropping below `1`.

### Time & Space Complexity

- **Time Complexity: `O(n)`** — We traverse the array once.
- **Space Complexity: `O(1)`** — We only use a few variables (`minVal` and `total`), regardless of the input size.

---

**Q5**:2040. K Radius SubArray Averages

Question can be found [here](https://leetcode.com/problems/k-radius-subarray-averages/description/)

**Solution**:

```js
def getAverages(nums, k):
    # If k = 0, each element is its own average
    if k == 0:
        return nums

    windowSize = 2 * k + 1
    n = len(nums)
    averages = [-1] * n

    # If the window is larger than the array
    if windowSize > n:
        return averages

    prefix = [nums[0]]

    for i in range(1, len(nums)):
        prefix.append(nums[i] + prefix[-1])

    # Calculate averages for valid indices
    for i in range(k, n - k):
        leftBound = i - k
        rightBound = i + k

        subArraySum = prefix[rightBound] - prefix[leftBound] + nums[leftBound]
        average = subArraySum // windowSize

        averages[i] = average

    return averages
```

### Time & Space Complexity

- **Time Complexity: `O(n)`** — We build the prefix-sum array in `O(n)` and then iterate through the valid indices in `O(n)`.
- **Space Complexity: `O(n)`** — The `prefix` array and `averages` array each use `O(n)` space.

**Overall:** `O(n)` time and `O(n)` space.

---

**Q6**: 1732.Find the highest Altitude

Question can be found [here](https://leetcode.com/problems/find-the-highest-altitude/)

**Solution**:

```js
def largestAltitude(gain):
    prefix = [0]

    for i in range(len(gain)):
        prefix.append(gain[i] + prefix[i])

    return max(prefix)
```

### Time & Space Complexity

- **Time Complexity: `O(n)`** — We traverse `gain` once to build the prefix array and `Math.max()` traverses it once.
- **Space Complexity: `O(n)`** — The `prefix` array stores `n + 1` altitude values.

---

**Q7**: 724. Find Pivot Index

Question can be found [here](https://leetcode.com/problems/find-pivot-index/description/)

**Solution**:

```js
def pivotIndex(nums):
    prefix = [nums[0]]

    for i in range(1, len(nums)):
        prefix.append(nums[i] + prefix[i - 1])

    for i in range(len(nums)):
        left = 0 if i == 0 else prefix[i - 1]
        right = prefix[len(nums) - 1] - prefix[i]

        if left == right:
            return i

    return -1
```

### Time & Space Complexity

- **Time Complexity: `O(n)`** — One loop builds the prefix sum and another loop checks the pivot index. `O(n) + O(n) = O(n)`.
- **Space Complexity: `O(n)`** — The `prefix` array stores `n` prefix-sum values.

---

**Q8**: 303.Range Sum SubQuery - Immutable

Question can be found [here](https://leetcode.com/problems/range-sum-query-immutable/description/)

**Solution**:

```js
class NumArray:
    def __init__(self, nums):
        self.prefix = [nums[0]]

        for i in range(1, len(nums)):
            self.prefix.append(self.prefix[i - 1] + nums[i])

    def sumRange(self, left, right):
        if left == 0:
            return self.prefix[right]

        return self.prefix[right] - self.prefix[left - 1]
```

### Time & Space Complexity

**Constructor:**

- **Time:** `O(n)` — Builds the prefix sum array.
- **Space:** `O(n)` — Stores `n` prefix-sum values.

**`sumRange(left, right)`:**

- **Time:** `O(1)` — Uses direct prefix-sum subtraction.
- **Space:** `O(1)` — No additional data structure is created.

### Overall

```bas
Preprocessing:  O(n) time, O(n) space
Each query:     O(1) time, O(1) space
```

