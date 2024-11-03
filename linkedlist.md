https://leetcode.com/problems/merge-k-sorted-lists/description/
more effecive with usage bunary heap
```js
var mergeKLists = function (lists) {
    const dummy = new ListNode()
    let curr = dummy

      let sortedLists = lists.filter(s=>!!s)
      while (sortedLists.length) {
        sortedLists = sortedLists.sort((a, b) => a.val - b.val)
        const min = sortedLists[0].val
        for (let i = 0; i < sortedLists.length && (i ==0 || sortedLists[i].val == min); i++) {
            curr.next = new ListNode(sortedLists[i].val)
            curr = curr.next
            sortedLists[i] = sortedLists[i].next
        }
        sortedLists = sortedLists.filter(s=>!!s)

    }
    return dummy.next
};
```

https://leetcode.com/problems/linked-list-cycle/description/
```js
// v1
var hasCycle = function(head) {
    const set = new Set()
    while(head){
        if(set.has(head)){
            return true
        }
        set.add(head) 
        head = head.next

    }
    return false
};
```

```js
// v2
var hasCycle = function(head) {
    let s = head
    let f = head
    while(s && f){
        s = s.next
        f = f.next?.next
        if(s === f){
            return true
        }
    }
    return false
};
```

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

https://leetcode.com/problems/add-two-numbers/description/
```js
var addTwoNumbers = function(l1, l2) {
    const head = new ListNode()
    let curr = head;
    let x = 0
    while(l1 || l2 || x){
       const sum = (l1?.val ?? 0) + (l2?.val ?? 0) + x
       curr.val = sum % 10
       x = sum >= 10 ? 1 : 0

       l1 = l1?.next
       l2 = l2?.next
       
       if(l1 || l2 || x){
          curr.next = new ListNode()
       }
       curr = curr.next       


    } 
    return head
};
```

```js
var addTwoNumbers = function(l1, l2) {
    const dummy = new ListNode()
    let curr = dummy;
    let x = 0
    while(l1 || l2 || x){
       const sum = (l1?.val ?? 0) + (l2?.val ?? 0) + x
       curr.next = new ListNode(sum % 10)
       x = sum >= 10 ? 1 : 0
       l1 = l1?.next
       l2 = l2?.next
       curr = curr.next       
    } 
    return dummy.next
};
```
