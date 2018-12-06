---
description: Reverse a linked list from position m to n.
---

# reverse linked list II

{% tabs %}
{% tab title="Notes" %}
Check possble null with awareness of given constraints !!! 

* If 1 ≤ m ≤ n ≤ length of list,  the code under comments  is not necessary.
{% endtab %}

{% tab title="Solution" %}
```java
public ListNode reverseBetween(ListNode head, int m, int n) {
    if (head == null || m >= n) {
        return head;
    }
    
    ListNode dummy = new ListNode(0);
    dummy.next = head;
    ListNode preM = dummy;
    
    for (int i = 1; i < m; i++) {
        //
        if (preM == null) {
            return null;
        }
        preM = preM.next;
    }
    
    //last preM and M may be null
    if (preM == null || preM.next == null) {
        return null;
    }
    
    //check preM, M
    ListNode M = preM.next, prev = M, cur = prev.next;
    
    for (int i = m; i < n; i++) {
        if (cur == null) { //check from M.next to N
            return null;
        }
        
        ListNode tmp = cur.next;
        cur.next = prev;
        prev = cur;
        cur = tmp;
    }
    preM.next = prev;
    M.next = cur;
    
    return dummy.next;
}
```
{% endtab %}
{% endtabs %}
