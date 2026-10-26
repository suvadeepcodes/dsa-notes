# Sliding Window

**Subarrays**: 

Given an array, a **subarray** is a contiguous section of the array. All the elements must be adjacent to each other in the original array and in their original order

**Valid Subarrays**: 

What makes a subarray valid ? 

1. A constraint metric. This is an attribute of a subarray.   - For example, the sum of the subarray, the number of unique elements in the subarray, the frequency of a specific element, etc.
2. A numeric restriction on the constraint metric.

Example ➡️ let's say a problem declares a subarray is valid if it has a sum less than or equal to `10`. The constraint metric here is the sum of the subarray, and the numeric restriction is `<= 10`. A subarray is considered valid if its constraint metric conforms to the numeric restriction, i.e., the sum is less than or equal to `10`

**Solving Problems with Sliding Window**:

- subarray + valid ➡️ think of sliding window 
- Type A Problems ➡️ best valid subarray , example : **longest** valid subarray
- Number of valid Subarrays

**Algorithm**:

```python
def fn(arr):
    left = 0

    for right in range(len(arr)):
        # Do some logic to "add" arr[right] to the window

        while WINDOW_IS_INVALID:
            # Do some logic to "remove" arr[left] from the window
            left += 1

        # Do some logic to update the answer
```

Time and Space Complexity : 

A sliding window guarantees a maximum of 2n window iterations - the right pointer can move n times and the left pointer can move n times. This means if the logic done for each window is O(1), sliding window algorithms run in O(n)

---

**Q1**: Given an array of positive integers `nums` and an integer `k`, find the length of the longest subarray whose sum is less than or equal to `k`

```js
def findLength(nums, k):
```

**Solution**:

```python
def findLength(nums, k):
    # curr is the current sum of the window
    left = 0
    curr = 0
    ans = 0

    for right in range(len(nums)):
        curr += nums[right]

        while curr > k:
            curr -= nums[left]
            left += 1

        ans = max(ans, right - left + 1)

    return ans
```

Time : O(n)

Space :O(1)

---

**Q2**: You are given a binary string `s` (a string containing only `"0"` and `"1"`). You may choose up to one `"0"` and flip it to a `"1"`. What is the length of the longest substring achievable that contains only `"1"`?

For example, given `s = "1101100111"`, the answer is `5`. If you perform the flip at index `2`, the string becomes `1111100111`.

```js
def findLength(s):
```

**Solution**:

```python
def findLength(s):
    # curr is the current number of zeros in the window
    left = 0
    curr = 0
    ans = 0

    for right in range(len(s)):
        if s[right] == "0":
            curr += 1

        while curr > 1:
            if s[left] == "0":
                curr -= 1
            left += 1

        ans = max(ans, right - left + 1)

    return ans
```

- Time and Space Complexity : 
  - Time : O(n)
  - Space :O(1) 

---

**Number of subarrays**: 

- Number of subarrays that fit some constraint = right - left + 1 

---

**Q3**: 713.Subarray Product Less Than K 

Question can be found [here](https://leetcode.com/problems/subarray-product-less-than-k/description/)

**Solution**:

```python
def numSubarrayProductLessThanK(nums, k):
    if k <= 1:
        return 0

    ans = 0
    left = 0
    curr = 1

    for right in range(len(nums)):
        curr *= nums[right]

        while curr >= k:
            curr //= nums[left]
            left += 1

        ans += right - left + 1

    return ans
```

Time : O(n)

Space :O(1)

---

## Fixed Window Size

```python
def fn(arr, k):
    curr = 0  # Some data to track the window

    # Build the first window
    for i in range(k):
        # Do something with curr or other variables
        pass

    ans = curr

    for i in range(k, len(arr)):
        # Add arr[i] to the window

        # Remove arr[i - k] from the window

        # Update ans
        pass

    return ans
```

**Q4**:Given an integer array `nums` and an integer `k`, find the sum of the subarray with the largest sum whose length is `k`.

```python
def findBestSubarray(nums, k):
  
```

**Solution**:

```python
def findBestSubarray(nums, k):
    curr = 0

    for i in range(k):
        curr += nums[i]

    ans = curr

    for i in range(k, len(nums)):
        curr += nums[i] - nums[i - k]
        ans = max(ans, curr)

    return ans
```

Time and Space Complexity : 

- The total for loop iterations is equal to n, where n is the length of `nums`, and the work done in each iteration is constant, giving this algorithm a time complexity of O(n), using O(1) space.

---

**Q5**:643. Maximum Average Subarray I

Question can be found [here](https://leetcode.com/problems/maximum-average-subarray-i/)

**Solution**:

```python
def findMaxAverage(nums, k):
    curr = 0

    for i in range(k):
        curr += nums[i]

    ans = curr

    for i in range(k, len(nums)):
        curr += nums[i] - nums[i - k]
        ans = max(ans, curr)

    return ans / k
```

**Time:** O(n) 

**Space:** O(1) 

---

**Q6**:1004. Max Consecutive Ones III

Question can be found [here](https://leetcode.com/problems/max-consecutive-ones-iii/)

**Solution**:

```python
def longestOnes(nums, k):
    left = 0
    curr = 0
    ans = 0

    for right in range(len(nums)):
        if nums[right] == 0:
            curr += 1

        while curr > k:
            if nums[left] == 0:
                curr -= 1
            left += 1

        ans = max(ans, right - left + 1)

    return ans
```

---

**Q7**:209.Minimum Size Subarray

Question can be found [here](https://leetcode.com/problems/minimum-size-subarray-sum/description/)

**Solution**:

```python
def minSubArrayLen(target, nums):
    left = 0
    curr = 0
    min_len = float("inf")

    for right in range(len(nums)):
        curr += nums[right]

        while curr >= target:
            min_len = min(min_len, right - left + 1)
            curr -= nums[left]
            left += 1

    return 0 if min_len == float("inf") else min_len
```

---

**Q8**:1456 Maximum Number of Vowels in a Substring of Given Length

Question can be found [here](https://leetcode.com/problems/maximum-number-of-vowels-in-a-substring-of-given-length/)

**Solution**:

```python
def maxVowels(s, k):
    curr = 0

    for i in range(k):
        if s[i] in "aeiou":
            curr += 1

    ans = curr

    for i in range(k, len(s)):
        if s[i] in "aeiou":
            curr += 1

        if s[i - k] in "aeiou":
            curr -= 1

        ans = max(ans, curr)

    return ans
```

---

**Q9**:1208. Get Equal Substrings Within Budget

Question can be found [here](https://leetcode.com/problems/get-equal-substrings-within-budget/)

**Solution**:

```python
def equalSubstring(s, t, maxCost):
    left = 0
    cost = 0
    ans = 0

    for right in range(len(s)):
        cost += abs(ord(s[right]) - ord(t[right]))

        while cost > maxCost:
            cost -= abs(ord(s[left]) - ord(t[left]))
            left += 1

        ans = max(ans, right - left + 1)

    return ans
```

