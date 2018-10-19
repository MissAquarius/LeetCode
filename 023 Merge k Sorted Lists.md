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
## <a name="Note">Note</a>
* 投机取巧的办法:首先将所有节点中的val加入到一个list中,然后用list的排序函数,排完序再转换成节点形式
* 链表这种数据结构,通常有个表头会方便很多,原因是:有表头的话,可以将第一个节点与其他节点同等对待,否则就要考虑头节点的单独处理.
**  比如此例中,要是没有表头,
那就得首先建立第一个节点,然后在循环中建立后面的节点,那么就得区分链表的长度是1吗?也就是说,有了表头,可以将后面的节点同等对待.
* 此题还有正规的最小堆的解法,后续补充.






