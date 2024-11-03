https://leetcode.com/problems/top-k-frequent-words/description/

try binary heap
```js
var topKFrequent = function(words, k) {
  const map = new Map()  
  for(let word of words){
    map.set(word, (map.get(word) ?? 0) + 1) 
  }
  const res = Array.from(map.entries()).toSorted((a, b) => {
      const cmp = b[1] - a[1]
      if(cmp == 0){
        return a[0].localeCompare(b[0])
      }
      return cmp

  }).slice(0, k).map((a) => a[0])
  return res
};
```

https://leetcode.com/problems/top-k-frequent-elements/description/
```js
var topKFrequent = function(nums, k) {
    const map = new Map()
    for(let num of nums){
        map.set(num, (map.get(num) ?? 0) + 1)
    }
    return Array.from(map.entries()).toSorted((a, b) => b[1] - a[1]).map((a) => a[0]).slice(0, k)
};
```
