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
// todo medium
```
