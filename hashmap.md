https://leetcode.com/problems/single-number/description/

```js
var singleNumber = function(nums) {
    return nums.reduce((a, v) => a ^ v)
};
```
