https://leetcode.com/problems/single-number/description/

```js
var singleNumber = function(nums) {
    return nums.reduce((a, v) => a ^ v)
};
```

https://leetcode.com/problems/two-sum/description/
```js
var twoSum = function(nums, target) {
    const map = {}
    for(let i=0; i < nums.length; i++){
        const v1 = nums[i]
        const v2 = target - nums[i]
        if(Number.isFinite(map[v2])){
            return [i, map[v2]]
        }
        map[v1] = i
    }
    return []
};
```
