# Two Pointers

### Core Idea ➡️

- Two pointers is an algorithm which involves having two integer variables that both move along an iterable
- There are several ways to implement two pointers

### Two Pointers Variant 1 ➡️

- Start the pointers at the edges of the input. Move them towards each other until they meet.

- Algorithm ➡️

  ```js
  function fn(arr) {
      let left = 0;
      let right = arr.length - 1;
  
      while (left < right) {
          // Do some logic here depending on the problem
  
          // Do some more logic to decide:
          // 1. left++
          // 2. right--
          // 3. Both left++ and right--
  
          if (/* condition */) {
              left++;
          } else if (/* condition */) {
              right--;
          } else {
              left++;
              right--;
          }
      }
  }
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
var checkIfPalindrome = function(s) {
    
}
```

**Solution**:

```js
var checkIfPalindrome = function(s) {
  let left = 0;
  let right = s.length - 1;
  while(left<right){
    if(s[left]!==s[right]){
      return false
    }
    left++;
    right-- 
  }
  return true
}


console.log(checkIfPalindrome("racecar"));
```

**Time:** O(n) — checks up to n/2 characters

**Space:** O(1) — only `left` and `right` pointers

---

**Q2**: Two Sum in Sorted Array

Given a **sorted** array of unique integers and a target integer, return `true` if there exists a pair of numbers that sum to target, `false` otherwise.

For example, given `nums = [1, 2, 4, 6, 8, 9, 14, 15]` and `target = 13`, return true because `4 + 9 = 13`.

```js
var checkForTarget = function(nums, target) {
}
```

**Solution**:

```js
var checkForTarget = function(nums, target) {
    let left = 0;
    let right = nums.length - 1;
    
    while (left < right) {
        // curr is the current sum
        let curr = nums[left] + nums[right];
        if (curr == target) {
            return true;
        }
        
        if (curr > target) {
            right--;
        } else {
            left++;
        }
    }
    
    return false;
}
```

Time and Space Complexity : 

- Time : O(n)
- Space : O(1)

**Q3**: 344.Reverse String 

Question can be found [here](https://leetcode.com/problems/reverse-string/description/)

**Solution**:

```js
var reverseString = function(s) {
   let left = 0;
   let right = s.length - 1;
   while(left<right){
    [s[left],s[right]]= [s[right],s[left]];
    left++;
    right--
   } 
};
```

**Q4**: 977.Squares of a Sorted Array

Question can be found [here](https://leetcode.com/problems/squares-of-a-sorted-array/description/)

**Solution**:

```js
var sortedSquares = function(nums) {
    let n = nums.length;
    let arr = new Array(nums.length).fill(0);
    let left = 0;
    let right = nums.length -1;
    for(let i=n-1;i>=0;i--){
        if(Math.abs(nums[left])>Math.abs(nums[right])){
            arr[i]= nums[left]*nums[left];
            left++;
        }else {
            arr[i]=nums[right]*nums[right];
            right--;
        }
    }
    return arr;
};
```

Time and Space Complexity : 

- Time : O(n)
- Space : O(n)

---

**Q5**:557. Reverse Words in a String Ⅲ

Question can be found [here](http://leetcode.com/problems/reverse-words-in-a-string-iii/description/)

**Solution**:

```js
var reverseWords = function(s) {
    let arr = s.split(" ");
    for(let i=0;i<arr.length;i++){
        arr[i]= reverse(arr[i]);
    }
    return arr.join(" ");
};

var reverse = function(str){
    let arr = str.split('');
    let left = 0;
    let right = arr.length - 1;
    while(left < right){
        [arr[left],arr[right]]= [[arr[right],arr[left]]
        left++;
        right--;
    }
    return arr.join('');
}
```

---

**Q6**:917.Reverse Only Letters

Question can be found [here](https://leetcode.com/problems/reverse-only-letters/description/)

**Solution**:

```js


 const isLetter =(c)=>{
    const lowerC = c.toLowerCase();
    const isAlpha = lowerC>="a" && lowerC<="z";
    return isAlpha;

}
var reverseOnlyLetters = function(s) {
    let arr = s.split("");
    let left =0;
    let right = s.length -1;
    while(left<right){
        const skipLeft = !isLetter(s[left]);
        if(skipLeft){
            left++;
            continue;
        }

        const skipRight =!isLetter(s[right]);
        if(skipRight){
            right--;
            continue;
        }

        [arr[left],arr[right]]=[arr[right],arr[left]];
        left++;
        right--;
    }

    return arr.join("");
};

```

---

**Q6**:2000.Reverse Prefix of Word

Question can be found [here](https://leetcode.com/problems/reverse-prefix-of-word/description/)

**Solution**:

```js

var reversePrefix = function(word, ch) {
    let i =0;
    for(let j=0;j<word.length;j++){
        if(word[j]===ch){
            i=j
            break;
        }  
    }
    if(i===word.length) return word;

    let l =0;
    let r =i;
    let arr = word.split("");
    while(l<r){
        [arr[l],arr[r]]=[arr[r],arr[l]];
        l++;
        r--;

    }
    return arr.join("");


    
};
```



---

### Two Pointers Variant 2 ➡️

- Move along both inputs simultaneously until all elements have been checked.

- Algorithm ➡️

  ```js
  function fn(arr1, arr2) {
    let i = 0;
    let j = 0;
  
    while (i < arr1.length && j < arr2.length) {
      // Do some logic here
  
      // Decide:
      // i++;
      // j++;
      // or both
    }
  
    while (i < arr1.length) {
      // Do some logic here
      i++;
    }
  
    while (j < arr2.length) {
      // Do some logic here
      j++;
    }
  }
  ```

  Time and Space Complexity : 

  - This method will have a linear time complexity of O(n+m)*O*(*n*+*m*) if the work inside the while loop is O(1)*O*(1), where `n = arr1.length` and `m = arr2.length`
  - This is because at every iteration, we move at least one pointer forward, and the pointers cannot be moved forward more than `n + m` times without the arrays being exhausted

### Problems on Variant 2 ➡️

**Q1**: Given two sorted integer arrays `arr1` and `arr2`, return a new array that combines both of them and is also sorted.

```js
var combine = function(arr1, arr2) {
}
```

**Solution**:

```js
var combine = function(arr1, arr2) {
    // ans is the answer
    let ans = [];
    let i = 0, j = 0;
    
    while (i < arr1.length && j < arr2.length) {
        if (arr1[i] < arr2[j]) {
            ans.push(arr1[i]);
            i++;
        } else {
            ans.push(arr2[j]);
            j++;
        }
    }
    
    while (i < arr1.length) {
        ans.push(arr1[i]);
        i++;
    }
    
    while (j < arr2.length) {
        ans.push(arr2[j]);
        j++;
    }
    
    return ans;
}
```

Time and Space Complexity ➡️

- Time : O(1)
- Space : O(1)

---

**Q2**: 392.Is Subsequence 

Question can be found [here](https://leetcode.com/problems/is-subsequence/description/)

**Solution**:

```js
var isSubsequence = function(s, t) {
    let i =0;
    let j =0;

    while(i<s.length && j < t.length){
        if(s[i]===t[j]){
            i++
        }
        j++
    }
    return i === s.length
};
```

Time and Space Complexity : 

- **Time:** O(n)
- **Space:** O(1)

---

**Q3**:2540.Minimum Common Value

Question can be found [here](https://leetcode.com/problems/minimum-common-value/description/)

**Solution**:

```js
var getCommon = function(nums1, nums2) {
    let i=0;
    let j=0;
    while(i<nums1.length && j<nums2.length){
        if(nums1[i]<nums2[j]){
            i++;
        }else if(nums1[i]>nums2[j]){
            j++;

        }else{
            return nums1[i]
        }
    }
    return -1;
};
```

---



---

### Two Pointers General Note 

- Two pointers just refers to using two integer variables to move along some iterables. The strategies we looked at in this article are the most common patterns, but always be on the lookout for a different way to approach a problem. There are even problems that make use of "three pointers".

### Problems 

**Q1**: 283. Move Zeroes

Question can be found [here](https://leetcode.com/problems/move-zeroes/description/)

**Solution**:

```js

var moveZeroes = function(nums) {
    let l =0;
    for(let r=0;r<nums.length;r++){
        if(nums[r]!==0){
            [nums[l],nums[r]]=[nums[r],nums[l]];
            l++
        }
    }
    
};
```





