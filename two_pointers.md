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
