https://leetcode.com/problems/merge-intervals/
```js
var merge = function(intervals) {
    intervals = intervals.toSorted((a , b)=> a[0] - b[0])
    const n = intervals.length
    const res = []
    let prevInt = intervals[0]
    let i = 1
    debugger;
    while(i < n) {
        const int = intervals[i]
        if(prevInt[1] >= int[0]){
             prevInt = [prevInt[0] , Math.max(prevInt[1], int[1] )]
        } else {
            res.push(prevInt)
            prevInt = int
        }
        i++
    }
    res.push(prevInt)
    return res
};
```
