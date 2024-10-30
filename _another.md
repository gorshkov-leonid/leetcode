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
