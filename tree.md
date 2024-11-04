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

https://leetcode.com/problems/balanced-binary-tree/description/
```js
function height(root){
    if(!root){
        return 0
    }
    const lh = height(root.left)
    const rh = height(root.right)
    if(lh == -1 || rh == -1 || Math.abs(lh - rh) > 1){
        return -1
    }
    return 1 + Math.max(lh, rh)
}


var isBalanced = function(root) {
    if(!root){
        return true
    }
    return height(root) >= 0
};
```

https://leetcode.com/problems/path-sum-ii/description/
```js
var pathSum = function(root, targetSum) {
    const res = []
    traverse(root, targetSum, [], res)
    return res
};

function traverse(root, targetSum, stack, res) {
    if(!root){
        return
    }
    stack.push(root)
    targetSum = targetSum - root.val
    if(!root.left && !root.right && targetSum == 0){
       res.push(stack.map(s => s.val))
    }
    traverse(root.left, targetSum, stack, res)
    traverse(root.right, targetSum, stack, res)
    stack.pop()
};
```
