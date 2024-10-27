https://leetcode.com/problems/binary-search/
```ts
function search(nums, target) {
    let a = 0, b = nums.length - 1, c, d
    while(a > -1 && b < nums.length && a <= b){
       c = (a+b) >>> 1
       d = nums[c]
       if(d == target){
           return c
       } else if(d < target){
           a = c + 1
       } else {
           b = c - 1
       }
    }
    return -1
};
```

https://leetcode.com/problems/guess-number-higher-or-lower/
```js
var guessNumber = function(n) {
    let a = 1
    let b = n
    let pick, res
    while(a <= b){
        pick = (a+b) >>> 1
        res = guess(pick)
        if(res === 0) {
            return pick
        } else if(res == 1){
            a = pick + 1
        } else {
            b = pick - 1
        }
    }
    return -1
};

```

https://leetcode.com/problems/search-a-2d-matrix/
```js
function searchMatrix(matrix,target) {
    const N = matrix.length
    const M = matrix[0].length
    const B =  N * M
    let a = 0, b = B - 1
    let i, j, c, v
    while(a >= 0 && b < B && a <= b){
       c = (a + b) >>> 1
       let i = Math.trunc(c / M)
       let j = c % M
       v = matrix[i][j]
       if(v == target){
           return true
       } else if(target > v){
           a = c + 1
       } else {
           b = c - 1
       }
    }
    return false
};

```

https://leetcode.com/problems/search-in-rotated-sorted-array/
```js
// `nums[c] < target` is important, or else you can get wrong case for `[1,3]` and `3`
var search = function(nums, target) {
    const n = nums.length
    let a = 0
    let b = n - 1
    while(a < b){
        let c = (a + b) >>> 1
        if(nums[0] <= nums[c]) {
            if(nums[0] <= target && target <= nums[c]){
               b = c 
            } else {
               a = c + 1
            }
        } else {
            if(nums[c] < target && target <= nums[n -1]){
               a = c + 1
            } else {
               b = c 
            }
        }
    }
    return nums[a] == target ? a : ( nums[b] == target ? b : -1)
};
```

https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/
```js
var findMin = function(nums) {
    let a = 0;
    let b = nums.length - 1
    let c
    if(nums[0] < nums[nums.length - 1]){
        return nums[0]
    }
    while(a < b){
        c = (a + b) >>> 1
        if(nums[b] < nums[c]){
            a = c + 1
        } else {
            b = c
        }
    }
     return nums[a]
};
```

https://leetcode.com/problems/search-in-rotated-sorted-array-ii/submissions/1435180321/
// wrong for `[1,0,1,1,1]` and `0`
```js
var search = function(nums, target) {
    let a = 0
    let b = nums.length - 1
    let c
    if(nums[a] === target){
        return true
    }
    if(nums[b] === target){
        return true
    }
    while(a < b) {
        c = (a + b) >>> 1 
        if(nums[0] < nums[c]){
            if(nums[0] <= target < nums[c]) {
                b = c
                if(nums[b] === target){
                    return true
                }
            } else {
                a = c + 1
                if(nums[a] === target){
                    return true
                }
            }
        } else {
            if(nums[c] <= target < nums[nums.length - 1]) {
                a = c + 1
                if(nums[a] === target){
                    return true
                }                
            } else {
                b = c
                if(nums[b] === target){
                    return true
                }
            }
        }
    }
    return false
};
```
