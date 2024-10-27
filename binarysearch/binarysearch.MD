https://leetcode.com/problems/binary-search/
```ts
function search(nums: number[], target: number): number {
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
var search = function(nums, target) {
    let a = 0
    let b = nums.length - 1
    let c
    while(a < b){
        c = (a + b) >>> 1
        if(nums[0] <= nums[c]) {
            if(nums[0] <= target && target <= nums[c]){
               b = c 
            } else {
               a = c + 1
            }
        } else {
            if(nums[c] <= target && target <= nums[nums.length -1]){
               a = c + 1
            } else {
               b = c 
            }
        }
    }
    return nums[c] == target ? c : -1
```

https://leetcode.com/problems/search-in-rotated-sorted-array/
```js
var search = function(nums, target) {
    let a = 0
    let b = nums.length - 1
    let c
    while(a < b){
        c = (a + b) >>> 1
        if(nums[0] <= nums[c]) {
            if(nums[0] <= target && target <= nums[c]){
               b = c 
            } else {
               a = c + 1
            }
        } else {
            if(nums[c] <= target && target <= nums[nums.length -1]){
               a = c + 1
            } else {
               b = c 
            }
        }
    }
    return nums[c] == target ? c : -1
};
```
