# [Reverse Nodes in k-Group](https://leetcode.com/problems/reverse-nodes-in-k-group/description/)

<!-- GFM-TOC -->
* <a href="#Description">Description</a>
* <a href="#Example">Example</a>
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->


## <a name="Description">Description</a>
>Given a linked list, reverse the nodes of a linked list k at a time and return its modified list.</br>
k is a positive integer and is less than or equal to the length of the linked list.</br>
If the number of nodes is not a multiple of k then left-out nodes in the end should remain as it is.</br>

## <a name="Example">Example</a>
>Input:</br>
Given this linked list: 1->2->3->4->5</br>
For k = 2, you should return: 2->1->4->3->5</br>
For k = 3, you should return: 3->2->1->4->5</br>


## <a name="Solution">Solution</a>
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    
     ## 反转函数 p指向组的前一个节点,q指向组的后一个节点
    def reverse1Group(self, start, end):
        self.gpre = start.next
        gcur = self.gpre.next
        
        while(gcur != end):
            self.gpre.next = gcur.next
            gcur.next = start.next
            start.next = gcur
            gcur = self.gpre.next
        return self.gpre
    
    def reverseKGroup(self, head, k):
        """
        :type head: ListNode
        :type k: int
        :rtype: ListNode
        """
        ## 加个表头
        result = ListNode(0)
        result.next = head
       
        ## 赋初值
        i = 0
        pre = result
        cur = head
        
        while(cur):
            i += 1            
            if i % k == 0:     ## 表示找到一组数,需要反转
                pre = self.reverse1Group(pre, cur.next)
                cur = pre.next
            else:
                cur = cur.next
                
        return result.next   
    
 ```
## <a name="Note">Note</a>
* 总体思路:用一个指针,从头开始遍历,同时计数,当计数发现指针扫过k个数的时候,说明找到了一组需要反转的k个数.将改组数丢进自定义的反转函数中,</br>
反转之后返回.继续向后遍历.
* 具体过程如下图所示:
* 同样,处理链表的问题时可加一个表头节点






