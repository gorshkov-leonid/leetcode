https://leetcode.com/problems/same-tree/
```js
var isSameTree = function(a, b) {
    if(a === b){
        return true
    }
    if(!a || !b || a.val !== b.val){
        return false
    }
    return isSameTree(a.left, b.left) && isSameTree(a.right, b.right) 
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
