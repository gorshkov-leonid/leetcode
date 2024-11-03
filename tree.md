https://leetcode.com/problems/same-tree/
```js
var isSameTree = function(p, q) {
    if(p === q){
        return true
    }
    if(!p || !q || p.val !== q.val){
        return false
    }
    return isSameTree(p.left, q.left) && isSameTree(p.right, q.right) 
};
```

https://leetcode.com/problems/symmetric-tree/
```js
const check = (a, b) => {
    if (a == b) {
        return true;
    }
    if (!a || !b || a.val != b.val) {
        return false;
    }
    return check(a.left, b.right) && check(a.right, b.left);
};

function isSymmetric(root) {
    return check(root.left, root.right);
}
```
