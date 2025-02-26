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

https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-transaction-fee/

https://www.youtube.com/watch?v=Ew_R-ZfhPEc

```js
var maxProfit = function(prices, fee) {
    const n = prices.length
    let profit = 0
    let spends = prices[0]
    for(let i = 0; i < n; i++){
        profit = Math.max(profit,  prices[i] - spends - fee)
        spends = Math.min(spends, prices[i] - profit)
    }
    return profit
};
```
or (https://algo.monster/liteproblems/714)

```js
var maxProfit = function(prices, fee) {
    const n = prices.length
    let sellOrWaitProfit = 0
    let holdOrBuy = -prices[0]
    for(let i = 0; i < n; i++){
        profit = Math.max(sellOrWaitProfit,  prices[i] + holdOrBuy - fee)
        spends = Math.max(holdOrBuy, sellOrWaitProfit - holdOrBuy[i])
    }
    return sellOrWaitProfit
};
```

```js
// with naming
var maxProfit = function(prices, fee) {
    const n = prices.length
    let sellOrWaitProfit = 0
    let holdOrBuyProfit = -prices[0]
    for(let i = 0; i < n; i++){
        sellOrWaitProfit = Math.max(sellOrWaitProfit,  prices[i] + holdOrBuyProfit - fee)
        holdOrBuyProfit = Math.max(holdOrBuyProfit, sellOrWaitProfit - prices[i])
    }
    return sellOrWaitProfit
};
```

https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/description/

https://www.youtube.com/watch?v=I7j0F7AHpb8
```js
function dfs(i, buy, prices, map) {
    const n = prices.length
    if (i >= n) {
        return 0
    }
    const cached = map.get(`${i}_${buy}`)
    if (Number.isFinite(cached)) {
        return cached
    }
    const cooldownProfit = dfs(i + 1, buy, prices, map)
    if (buy) {
        const buyingProfit = dfs(i + 1, !buy, prices, map) - prices[i]
        const profit = Math.max(cooldownProfit, buyingProfit)
        map.set(`${i}_${buy}`, profit)
        return profit
    } else {
        const sellingProfit = dfs(i + 2, !buy, prices, map) + prices[i]
        const profit = Math.max(cooldownProfit, sellingProfit)
        map.set(`${i}_${buy}`, profit)
        return profit
    }
}


var maxProfit = function (prices) {
    const map = new Map()
    return dfs(0, true, prices, map)
};
```
