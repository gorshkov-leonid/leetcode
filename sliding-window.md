https://leetcode.com/problems/sliding-window-median/description/
timeout on 30 / 43
```js
function addToRes(res, sortedBuffer, k, isOdd){
    if(isOdd){
        res.push(sortedBuffer[k >>> 1])
    } else {
        res.push(((sortedBuffer[(k >>> 1) - 1] ?? 0) + sortedBuffer[(k >>> 1)]) / 2)
    }
}

var medianSlidingWindow = function(nums, k) {
    const n = nums.length
    const isOdd = k % 2
    const res = []
    const buffer = []
    
    if(n < k){
        return []
    }
    for(let i = 0; i < k; i++){
       buffer.push(nums[i])
    }
    debugger;
    let sortedBuffer = buffer.toSorted((a, b)=> a - b)
    addToRes(res, sortedBuffer, k, isOdd)
    for(let i = k; i < n; i++){
       buffer.shift()
       buffer.push(nums[i])
       sortedBuffer = buffer.toSorted((a, b)=> a - b)
       addToRes(res, sortedBuffer, k, isOdd)
    }
    return res
};

```

https://leetcode.com/problems/sliding-window-maximum/description/
```js
// todo hard
```

https://leetcode.com/problems/longest-repeating-character-replacement/description/
```js
var characterReplacement = function(s, k) {
    let ans = 0;
    let n = s.length;
    for (let c = 65; c <= 90; c++) { // ASCII values for 'A' to 'Z'
        let i = 0, j = 0, replaced = 0;
        while (j < n) {
            if (s.charCodeAt(j) === c) {
                j++;
            } else if (replaced < k) {
                j++;
                replaced++;
            } else if (s.charCodeAt(i) === c) {
                i++;
            } else {
                i++;
                replaced--;
            }
            ans = Math.max(ans, j - i);
        }
    }
    return ans;
};
```
