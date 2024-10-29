https://leetcode.com/problems/single-number/submissions/1437050884/

```js
var singleNumber = function(nums) {
    return nums.reduce((a, v) => a ^ v)
};
```
