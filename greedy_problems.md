https://leetcode.com/problems/best-time-to-buy-and-sell-stock/description/
```js
var maxProfit = function(prices) {
    let l = 0
    let r = 0
    const n = prices.length
    let max = 0
    while(r < n){
      if(prices[l] < prices[r]){
          max = Math.max(max, prices[r] - prices[l])
      }
      else {
          l = r
      }
      r++
    }
    return max
};
```

https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/
```js
var maxProfit = function(prices) {
    const n = prices.length
    let sum = 0
    for(let i = 1; i < n; i++){
        const delta = prices[i] - prices[i - 1]
        if(delta > 0){
           sum += delta
        }
    }
    return sum
};
```
