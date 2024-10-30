```js
function gen_parens(n, prefix, opened, closed){
    if(prefix.length == 2*n){
        process.stdout.write(prefix+"\n")
        return
    }
    if(opened < n){
        gen_parens(n, prefix+"(", opened + 1, closed)
    }
    if(closed < opened){
        gen_parens(n, prefix+")", opened, closed + 1)
    }
}
for (let k = 0; k < 5; k++){
    gen_parens(k, "", 0, 0, 0)
}
```

https://leetcode.com/problems/minimum-remove-to-make-valid-parentheses/description/
```js
var minRemoveToMakeValid = function(s) {
    const ss = s.split('')
    const st = []
    for(let i = 0; i < ss.length; i++){
      const c = ss[i]  
      if(c === '('){
        st.push(i)
      } else if(c === ')'){
        if(!st.length){
            ss[i] = ""
        } else {
            st.pop()
        }
      }
    }
    for(i of st){
        ss[i] = ""
    }
    return ss.join("")
};
```
