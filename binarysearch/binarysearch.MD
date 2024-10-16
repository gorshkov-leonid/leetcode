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
