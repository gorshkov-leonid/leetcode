https://leetcode.com/problems/valid-parentheses/description/
```js
var isValid = function(s) {
    let stack = []
    const open = ["(", "[", "{"]
    const close = [")", "]", "}"]
    for(let c of s){
        if(open.includes(c)){
             stack.push(c)
        } else {
            if(!stack.length){
                return false
            }
            if(c === ")" && stack[stack.length - 1] !== "(") {
                return false
            }
            if(c === "]" && stack[stack.length - 1] !== "[") {
                return false
            }
            if(c === "}" && stack[stack.length - 1] !== "{") {
                return false
            }
            stack.pop()
        }
    }
    return !stack.length
}
```
