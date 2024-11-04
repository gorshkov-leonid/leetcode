https://leetcode.com/problems/number-of-islands/description/
```js
// rewrite
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

```js
// dfs with recursion
function dfs(i, j, n, m, grid, visited){
    if(visited[i][j] === '1'){
        return
    }
    if(grid[i][j] === '0'){
        visited[i][j] = '1'
        return
    }
    visited[i][j] = '1'
    if(i < n - 1){
        dfs(i + 1, j, n, m, grid, visited)
    }
    if(j > 0){
        dfs(i, j - 1, n, m, grid, visited)
    }
    if(i > 0){
        dfs(i - 1, j, n, m, grid, visited)
    }
    if(j < m - 1){
        dfs(i, j + 1, n, m, grid, visited)
    }


}

var numIslands = function (grid) {
    if (!grid.length) {
        return 0
    }
    const n = grid.length
    const m = grid[0].length

    const visited = new Array(n)
    for(let i = 0; i < visited.length; i++){
        visited[i] = new Array(m).fill('0')
    }

    let k = 0

    for (let i = 0; i < n; i++) {
        for (let j = 0; j < m; j++) {
            if(grid[i][j] === '0' || visited[i][j] === '1'){
                continue;
            }
            dfs(i, j, n, m, grid, visited)
            k++
        }
    }
    return k
};
```
