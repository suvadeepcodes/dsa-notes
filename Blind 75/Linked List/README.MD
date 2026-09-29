# Linked List

Anki ➡️ 06-linked-list

**Q1**: *Reverse Linked List*

Question can be found [here](https://leetcode.com/problems/reverse-linked-list/description/)

**Solution**:

```python
class Solution:
    def reverseList(self, head: ListNode | None) -> ListNode | None:
        prev , curr = None , head
        while curr:
            nxt = curr.next
            curr.next = prev
            prev = curr
            curr = nxt
        return prev
```

Time :O(1)

Space : O(1)
