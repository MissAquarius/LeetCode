# [Merge k Sorted Lists](https://leetcode.com/problems/merge-k-sorted-lists/description/)

<!-- GFM-TOC -->
* <a href="#Description">Description</a>
* <a href="#Example">Example</a>
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->


## <a name="Description">Description</a>
>Merge k sorted linked lists and return it as one sorted list. Analyze and describe its complexity.</br>

## <a name="Example">Example</a>
>Input:</br>
[</br>
  1->4->5,</br>
  1->3->4,</br>
  2->6</br>
]</br>
Output: 1->1->2->3->4->4->5->6</br>

## <a name="Solution">Solution</a>
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def mergeKLists(self, lists):
        """
        :type lists: List[ListNode]
        :rtype: ListNode
        """
        temp = []
        for i in range(len(lists)):
            p = lists[i]
            while(p!=None):
                temp.append(p.val)
                p = p.next
        
        temp.sort()
        
        if len(temp) == 0:
            return []
        ## result是指向表头节点
        result = ListNode(0)
        q = result
        
        for i in range(len(temp)):
            q.next = ListNode(temp[i])
            q = q.next 
          
        return result.next
    
 ```
 ```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def merge2Lists(self, list1, list2):
        
        if list1 == None:
            return list2 
        if list2 == None:
            return list1  
 
        ## 加一个表头
        DummyNode = ListNode(-1)
        DummyNode.next = None
        
        cur = DummyNode
        
        while(list1 and list2):
            if list1.val < list2.val:
                cur.next = list1
                list1 = list1.next
            else:
                cur.next = list2
                list2 = list2.next
            cur = cur.next
        
        if list1 == None:
            cur.next = list2
        if list2 ==  None:
            cur.next = list1
        print(cur.val)    
        return DummyNode.next
    
    def mergeKLists(self, lists):
        """
        :type lists: List[ListNode]
        :rtype: ListNode
        """
        ## 分治法
        length = len(lists)
        if length == 0:
            return None
        
        while(length > 1):
            half = (length + 1 )// 2
            for i in range(0, length//2):
                lists[i] = self.merge2Lists(lists[i], lists[i+half])
            length = half
        return lists[0]
        
    
 ```
## <a name="Note">Note</a>
* 投机取巧的办法:首先将所有节点中的val加入到一个list中,然后用list的排序函数,排完序再转换成节点形式
* 链表这种数据结构,通常有个表头会方便很多,原因是:有表头的话,可以将第一个节点与其他节点同等对待,否则就要考虑头节点的单独处理.
  * 比如此例中,要是没有表头,那就得首先建立第一个节点,然后在循环中建立后面的节点,那么就得区分链表的长度是1吗?也就是说,有了表头,可以将后面的节点同等对待.
* 分治法:
  * 分治法中遇到困难的是对于list长度是奇数和偶数的处理.即为什么half = (length + 1 )// 2 与在循环中i in range(0, length//2).自己画图即可证明,这里也常用于对奇偶情况的处理.如找一半的长度,将原长度+1再平均
* 最小堆法:






