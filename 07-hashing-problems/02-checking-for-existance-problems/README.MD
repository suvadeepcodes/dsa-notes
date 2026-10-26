# Checking for existance Problems

## Hash Maps & Sets: Checking Existence

- Purpose ➡️ Efficiently check whether an element exists.
- Array ➡️ \(O(n)\) search.
- Hash Map / Set ➡️ Average \(O(1)\) lookup.
- Impact on DSA ➡️ Can often reduce time complexity from \(O(n^2)\) to \(O(n)\).
- Key Takeaway ➡️ Use a hash set when you only need to track existence; use a hash map when you need to associate keys with values.

**Q**: Two Sum 

Question can be found [here](https://leetcode.com/problems/two-sum/description/)

**Solution**:

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        dic = {}
        for i in range(len(nums)):
            num = nums[i]
            complement = target - num
            if complement in dic: # This operation is O(1)!
                return [i, dic[complement]]
            
            dic[num] = i
        
        return [-1, -1]
```

**Q**: First Letter to Appear Twice 

Question can be found [here](https://leetcode.com/problems/first-letter-to-appear-twice/description/)

**Solution**:

```python
class Solution:
    def repeatedCharacter(self, s: str) -> str:
        seen = set()
        for c in s:
            if c in seen:
                return c
            seen.add(c)

        return " "
```

**Q**: Given an integer array `nums`, find all the numbers `x` in `nums` that satisfy the following: `x + 1` is not in `nums`, and `x - 1` is not in `nums`.

If a valid number `x` appears multiple times, you only need to include it in the answer once.

**Solution**:

```python
def find_numbers(nums):
    ans = []
    nums_set = set(nums)

    for num in nums_set:
        if (num + 1 not in nums_set) and (num - 1 not in nums_set):
            ans.append(num)
    
    return ans
```

Note ➡️ Anytime you find your algorithm running `if ... in ...`, then consider using a hash map or set to store elements to have these operations run in O(1)

**Q**: Check if the Sentence is Pangram 

Question can be found [here](https://leetcode.com/problems/check-if-the-sentence-is-pangram/description/)

**Solution**:

```python
def checkIfPangram(self, sentence: str) -> bool:
        my_set = set(sentence)
        return len(my_set) == 26
```

**Q**: Missing Number 

Question can be found [here](https://leetcode.com/problems/missing-number/description/)

**Solution**:

```python
def missingNumber(self, nums: List[int]) -> int:
        num_set = set(nums)
        n = len(nums)

        for number in range(n + 1):
            if number not in num_set:
                return number
```

**Q**: Counting Elements

Question can be found [here](https://leetcode.com/problems/counting-elements/description/)

**Solution**:

```python
def countElements(self, arr: List[int]) -> int:
        num_set = set(arr)
        count = 0

        for num in arr:
            if num + 1 in num_set:
                count += 1

        return count
```

