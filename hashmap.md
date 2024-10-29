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

https://leetcode.com/problems/4sum/
```js
const fourSum = function (nums, target) {

    var twoSum = function(start, target) {
        const set = new Set()
        const res = []
        for(let i=start; i < nums.length; i++){
            const v1 = nums[i]
            if(res.length && v1 === res[res.length - 1][1]){
               continue;
            }            
            const v2 = target - nums[i]
            if(set.has(v2)){
                res.push([v2, v1])
            }
            set.add(v1)
        }
        return res
    };

    function kSum(start, target, k) {
        let averageValue = Math.floor(target / k);
        if (start === nums.length || nums[start] > averageValue || averageValue > nums[nums.length - 1]) {
            return res;
        }
        if(k === 2) {
            return twoSum(start, target)
        }
        let res = [];
        for(let i = start; i < nums.length; i++){
            if(i ==start || nums[i] != nums[i - 1]){
                kSum(i + 1, target - nums[i], k - 1).forEach((v)=> {
                     res.push([nums[i]].concat(v))
                })
            }
        }
        return res
    }
    nums.sort((a, b) => a - b);
    return kSum(0, target, 4);
};
```

https://leetcode.com/problems/group-anagrams/
```js
var groupAnagrams = function(strs) {
    const map = new Map()
    for(let str of strs){
        const sorted = str.split('').sort().join('')
        let words = map.get(sorted)
        if(!words){
           map.set(sorted, words = [])
        }
        words.push(str)
    }
    return Array.from(map.values())
};
```

https://leetcode.com/problems/valid-anagram/
```js
var isAnagram = function(s, t) {
    if(s.length !== t.length){
        return false
    }
    const map = new Map()
    for(let i = 0; i < s.length; i++){
        const c = s.charCodeAt(i)
        map.set(c, (map.get(c) ?? 0) + 1)
    }
    for(let i = 0; i < t.length; i++){
        const c = t.charCodeAt(i)
        const count = map.get(c)
        if(count === undefined){
            return false
        }
        map.set(c, count - 1)
    }
    return Array.from(map.values()).every(s => s === 0)
};
```
