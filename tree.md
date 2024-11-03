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
const check = (root1, root2) => {
    if (root1 == root2) {
        return true;
    }
    if (root1 == null || root2 == null || root1.val != root2.val) {
        return false;
    }
    return check(root1.left, root2.right) && check(root1.right, root2.left);
};

function isSymmetric(root) {
    return check(root.left, root.right);
}

```
