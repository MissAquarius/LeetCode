# [Remove Duplicates from Sorted List](https://leetcode.com/problems/remove-duplicates-from-sorted-list/description/)

<!-- GFM-TOC -->
* <a href="#Description">Description</a>
* <a href="#Example">Example</a>
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->


## <a name="Description">Description</a>
>Given a sorted linked list, delete all duplicates such that each element appear only once.</br>

## <a name="Example">Example</a>
>Input: 1->1->2</br>
Output: 1->2</br>

>Input: 1->1->2->3->3</br>
Output: 1->2->3</br>

## <a name="Solution">Solution</a>
```python
# -*- coding: utf-8 -*-
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def deleteDuplicates(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        ## 加一个表头
        dummy = ListNode(-2)  ## 表头初始化这里本来是-1,结果有个case是以-1打头的,因此改成-2了,感觉很魔性……
        dummy.next = None
        
        p = head
        q = dummy 
        
        while(p != None):
            if(p.val != q.val):
                temp = ListNode(p.val)
                temp.next = None
                q.next = temp
                q = temp
            p = p.next
        ```
        while(p != None):
            if(p.val != q.val):
                q.next = p
                q = p
            p = p.next
        q.next = None 
       ```
        return dummy.next
        

``` 
## <a name="Note">Note</a>
* 连接时,本来想的是与原链表直接相连,但是这样最后一个数字重复时,会有错.因此是新建ListNode相连.
* 或者是直接与原链表相连,最后强制q的next是空
  






