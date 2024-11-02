https://leetcode.com/problems/reverse-linked-list/description/
```js
var reverseList = function(head) {
    if(!head){
        return head
    }
    let prev = head
    let curr = head.next
    prev.next = null
    while(curr){
        const next = curr.next 
        curr.next = prev
        prev = curr
        curr = next
    }
    return prev
};
```
