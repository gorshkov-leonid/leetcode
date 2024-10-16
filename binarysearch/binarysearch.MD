https://leetcode.com/problems/binary-search/
```ts
function search(nums: number[], target: number): number {
    let a = 0
    let b = nums.length - 1
    let c = 0
    while(a > -1 && b < nums.length && a <= b){
       c = Math.trunc((a+b) / 2) 
       if(nums[c] == target){
           return c
       } else if(nums[c] < target){
           a = c + 1
       } else if(nums[c] > target){
           b = c - 1
       }
    }
    return -1
};

function search(nums: number[], target: number): number {
    const L = nums.length
    let a = 0, b = L - 1, m, d
    while(a > -1 && b < L && a <= b){
       m = (a+b) >>> 1
       d = nums[m]
       if(d == target){
           return m
       } else if(d < target){
           a = m + 1
       } else {
           b = m - 1
       }
    }
    return -1
};
```
