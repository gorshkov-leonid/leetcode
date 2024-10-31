https://leetcode.com/problems/container-with-most-water/description/
```js
var maxArea = function(height) {
      let a = 0
      let b = height.length - 1
      let max = 0

      while(a < b){
        const vA = height[a]
        const vB = height[b]
         const s = Math.min(vA, vB) * (b - a)
         if(s > max){
            max = s
         }
         if(vA <= vB) {
            a += 1
         }
         else {
            b -= 1
         }
      }
      return max
}
```

https://leetcode.com/problems/partition-labels/description/
```js
var partitionLabels = function(s) {
    let map = {}
    for(let i = 0; i < s.length; i++){
         map[s.charAt(i)] = i
    }
    let l = 0
    let r = 0
    const res = [] 
    let max = 0
    while(r < s.length) {
        const c = s.charAt(r)
        max = Math.max(map[c], max)
        if(max === r){
            r++
            res.push(r - l)
            l = r
        } else {
            r++
        }
    }
    return res
};
```
