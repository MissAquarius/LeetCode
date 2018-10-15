# [Remove Nth Node From End of List](https://leetcode.com/problems/remove-nth-node-from-end-of-list/description/)

<!-- GFM-TOC -->
* <a href="#Description">Description</a>
* <a href="#Example">Example</a>
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->


## <a name="Description">Description</a>
>Given a linked list, remove the n-th node from the end of list and return its head.</br>

## <a name="Example">Example</a>
>Given linked list: 1->2->3->4->5, and n = 2.</br>
After removing the second node from the end, the linked list becomes 1->2->3->5.</br>


## <a name="Solution">Solution</a>
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def removeNthFromEnd(self, head, n):
        """
        :type head: ListNode
        :type n: int
        :rtype: ListNode
        """       
        ## 有点类似滑动窗口,窗口内有n+1个节点.不断地后移窗口,直到窗口的右边是尾节点,此时窗口的左边是待删除节点的前一个节点
        ## 特殊情况：如果链表长度为n且删除倒数第n个节点时,即只有n个节点删除首节点.此时窗口的右边应该是指向一个空节点,直接将表头指向后一个节点即可
        
        q = head 
        p = head 
        
        for i in range(n):
            q = q.next

        ## 特殊情况
        if q == None:
            return p.next
                    
        ## 一般情况
        while( q.next != None):
            p = p.next
            q = q.next        
        p.next = p.next.next
        
        return head  
 ```
 
## <a name="Note">Note</a>
* 注意特殊情况(粑粑的思路:快慢指针)





