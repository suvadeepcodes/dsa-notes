# 1732.Find the highest Altitude

Question can be found [here](https://leetcode.com/problems/find-the-highest-altitude/description/)

**Solution**:

```js
var largestAltitude = function(gain) {
    let prefix = [0];
    for(let i=0;i<gain.length;i++){
        prefix.push(gain[i]+prefix[prefix.length-1])
    }

    let max = -Infinity;
    for(let i=0;i<prefix.length;i++){
        if(prefix[i]>max){
            max=prefix[i]
        }
    }
    return max;
};
```

- Time and Space Complexity 
  - Time :
  - Space : 