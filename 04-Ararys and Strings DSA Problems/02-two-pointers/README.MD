# Two Pointers

### Core Idea ➡️

- Two pointers is an algorithm which involves having two integer variables that both move along an iterable
- There are several ways to implement two pointers

### Two Pointers Variant 1 ➡️

- Start the pointers at the edges of the input. Move them towards each other until they meet.

- Algorithm ➡️

  ```python
  def fn(arr):
      left = 0
      right = len(arr) - 1
  
      while left < right:
          # Do some logic here depending on the problem
  
          # Do some more logic to decide:
          # 1. left += 1
          # 2. right -= 1
          # 3. Both left += 1 and right -= 1
  
          if condition1:
              left += 1
          elif condition2:
              right -= 1
          else:
              left += 1
              right -= 1
  ```
  
  Time Complexity : 
  
  - We will never have more than O(n)*O*(*n*) iterations for the while loop because the pointers start n*n* away from each other and move at least one step closer in every iteration.
  - Therefore, if we can keep the work inside each iteration at O(1)*O*(1), this technique will result in a linear runtim

---

### Problems on Variant 1 

**Q1**: Is String Palindrome 

Given a string `s`, return `true` if it is a palindrome, `false` otherwise.

A string is a palindrome if it reads the same forward as backward. That means, after reversing it, it is still the same string. For example: "abcdcba", or "racecar".

```js
def checkIfPalindrome(s):
```

**Solution**:

```python
def checkIfPalindrome(s):
    left = 0
    right = len(s) - 1

    while left < right:
        if s[left] != s[right]:
            return False

        left += 1
        right -= 1

    return True


print(checkIfPalindrome("racecar"))
```

**Time:** O(n) — checks up to n/2 characters

**Space:** O(1) — only `left` and `right` pointers

---

**Q2**: Two Sum in Sorted Array

Given a **sorted** array of unique integers and a target integer, return `true` if there exists a pair of numbers that sum to target, `false` otherwise.

For example, given `nums = [1, 2, 4, 6, 8, 9, 14, 15]` and `target = 13`, return true because `4 + 9 = 13`.

```python
def checkForTarget(nums, target):
```

**Solution**:

```python
def checkForTarget(nums, target):
    left = 0
    right = len(nums) - 1

    while left < right:
        # curr is the current sum
        curr = nums[left] + nums[right]

        if curr == target:
            return True

        if curr > target:
            right -= 1
        else:
            left += 1

    return False
```

Time and Space Complexity : 

- Time : O(n)
- Space : O(1)

**Q3**: 344.Reverse String 

Question can be found [here](https://leetcode.com/problems/reverse-string/description/)

**Solution**:

```js
def reverseString(s):
    left = 0
    right = len(s) - 1

    while left < right:
        s[left], s[right] = s[right], s[left]
        left += 1
        right -= 1
```

**Q4**: 977.Squares of a Sorted Array

Question can be found [here](https://leetcode.com/problems/squares-of-a-sorted-array/description/)

**Solution**:

```python
def sortedSquares(nums):
    n = len(nums)
    arr = [0] * n

    left = 0
    right = n - 1

    for i in range(n - 1, -1, -1):
        if abs(nums[left]) > abs(nums[right]):
            arr[i] = nums[left] * nums[left]
            left += 1
        else:
            arr[i] = nums[right] * nums[right]
            right -= 1

    return arr
```

Time and Space Complexity : 

- Time : O(n)
- Space : O(n)

---

**Q5**:557. Reverse Words in a String Ⅲ

Question can be found [here](http://leetcode.com/problems/reverse-words-in-a-string-iii/description/)

**Solution**:

```python
def reverseWords(s):
    arr = s.split(" ")

    for i in range(len(arr)):
        arr[i] = reverse(arr[i])

    return " ".join(arr)


def reverse(str):
    arr = list(str)
    left = 0
    right = len(arr) - 1

    while left < right:
        arr[left], arr[right] = arr[right], arr[left]
        left += 1
        right -= 1

    return "".join(arr)
```

---

**Q6**:917.Reverse Only Letters

Question can be found [here](https://leetcode.com/problems/reverse-only-letters/description/)

**Solution**:

```js


 def isLetter(c):
    lowerC = c.lower()
    isAlpha = "a" <= lowerC <= "z"
    return isAlpha


def reverseOnlyLetters(s):
    arr = list(s)
    left = 0
    right = len(s) - 1

    while left < right:
        skipLeft = not isLetter(s[left])
        if skipLeft:
            left += 1
            continue

        skipRight = not isLetter(s[right])
        if skipRight:
            right -= 1
            continue

        arr[left], arr[right] = arr[right], arr[left]
        left += 1
        right -= 1

    return "".join(arr)


print(reverseOnlyLetters("ab-cd"))
print(reverseOnlyLetters("a-bC-dEf-ghIj"))
```

---

**Q6**:2000.Reverse Prefix of Word

Question can be found [here](https://leetcode.com/problems/reverse-prefix-of-word/description/)

**Solution**:

```python

def reversePrefix(word, ch):
    i = 0

    for j in range(len(word)):
        if word[j] == ch:
            i = j
            break
    else:
        return word

    l = 0
    r = i
    arr = list(word)

    while l < r:
        arr[l], arr[r] = arr[r], arr[l]
        l += 1
        r -= 1

    return "".join(arr)
    
```



---

### Two Pointers Variant 2 ➡️

- Move along both inputs simultaneously until all elements have been checked.

- Algorithm ➡️

  ```js
  def fn(arr1, arr2):
      i = 0
      j = 0
  
      while i < len(arr1) and j < len(arr2):
          # Do some logic here
  
          # Decide:
          # i += 1
          # j += 1
          # or both
  
      while i < len(arr1):
          # Do some logic here
          i += 1
  
      while j < len(arr2):
          # Do some logic here
          j += 1
  ```
  
  Time and Space Complexity : 
  
  - This method will have a linear time complexity of O(n+m)*O*(*n*+*m*) if the work inside the while loop is O(1)*O*(1), where `n = arr1.length` and `m = arr2.length`
- This is because at every iteration, we move at least one pointer forward, and the pointers cannot be moved forward more than `n + m` times without the arrays being exhausted

### Problems on Variant 2 ➡️

**Q1**: Given two sorted integer arrays `arr1` and `arr2`, return a new array that combines both of them and is also sorted.

```js
def combine(arr1, arr2):
    
```

**Solution**:

```python
ef combine(arr1, arr2):
    i = 0
    j = 0
    result = []

    while i < len(arr1) and j < len(arr2):
        if arr1[i] < arr2[j]:
            result.append(arr1[i])
            i += 1
        else:
            result.append(arr2[j])
            j += 1

    while i < len(arr1):
        result.append(arr1[i])
        i += 1

    while j < len(arr2):
        result.append(arr2[j])
        j += 1

    return result
```

Time and Space Complexity ➡️

- Time : O(1)
- Space : O(1)

---

**Q2**: 392.Is Subsequence 

Question can be found [here](https://leetcode.com/problems/is-subsequence/description/)

**Solution**:

```js
def isSubsequence(s, t):
    i = 0
    j = 0

    while i < len(s) and j < len(t):
        if s[i] == t[j]:
            i += 1
        j += 1

    return i == len(s)
```

Time and Space Complexity : 

- **Time:** O(n)
- **Space:** O(1)

---

**Q3**:2540.Minimum Common Value

Question can be found [here](https://leetcode.com/problems/minimum-common-value/description/)

**Solution**:

```python
def getCommon(nums1, nums2):
    i = 0
    j = 0

    while i < len(nums1) and j < len(nums2):
        if nums1[i] < nums2[j]:
            i += 1
        elif nums1[i] > nums2[j]:
            j += 1
        else:
            return nums1[i]

    return -1
```

---



---

### Two Pointers General Note 

- Two pointers just refers to using two integer variables to move along some iterables. The strategies we looked at in this article are the most common patterns, but always be on the lookout for a different way to approach a problem. There are even problems that make use of "three pointers".

### Problems 

**Q1**: 283. Move Zeroes

Question can be found [here](https://leetcode.com/problems/move-zeroes/description/)

**Solution**:

```python
def moveZeroes(nums):
    l = 0

    for r in range(len(nums)):
        if nums[r] != 0:
            nums[l], nums[r] = nums[r], nums[l]
            l += 1

```





