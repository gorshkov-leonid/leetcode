https://leetcode.com/problems/number-of-islands/description/
```js
var numIslands = function(grid) {
    const n = grid.length
    const m = grid[0].length
    let count = 0
    for(let i = 0; i < n; i++){
        for(let j = 0; j < m; j++){
            if(grid[i][j] === "1"){
                count += 1
                clearIsland(grid, i, j, n, m)
            }
        }
    }
    return count
};

function clearIsland(grid, i, j, n, m){
      grid[i][j] = "0"
      if(i > 0 &&  grid[i - 1][j] === "1"){
        clearIsland(grid, i - 1, j, n, m)
      }
      if(i < n - 1 &&  grid[i + 1][j] === "1"){
        clearIsland(grid, i + 1, j, n, m)
      }
      if(j > 0 &&  grid[i][j - 1] === "1"){
        clearIsland(grid, i, j - 1, n, m)
      }
      if(j < m - 1 &&  grid[i][j + 1] === "1"){
        clearIsland(grid, i, j + 1, n, m)
      }
}

```
