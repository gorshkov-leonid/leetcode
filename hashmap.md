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
        const v = nums[i]
        map[v] = i
    }
    for(let i=0; i < nums.length; i++){
        const v = target - nums[i]
        const j = map[v]
        if(j != i && Number.isFinite(map[v])){
            return [i, map[v]]
        }
    }
    return []
};
```
