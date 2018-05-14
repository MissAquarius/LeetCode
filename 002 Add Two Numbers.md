# [Add Two Numbers](https://leetcode.com/problems/add-two-numbers/description/)

<!-- GFM-TOC -->
* <a href="#Description">Description</a>
* <a href="#Example">Example</a>
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->


## <a name="Description">Description</a>
>You are given two non-empty linked lists representing two non-negative integers.</br>
The digits are stored in reverse order and each of their nodes contain a single digit.</br>
Add the two numbers and return it as a linked list.</br>
You may assume the two numbers do not contain any leading zero, except the number 0 itself.</br>

## <a name="Example">Example</a>
>Input: (2 -> 4 -> 3) + (5 -> 6 -> 4) </br>
Output: 7 -> 0 -> 8</br>
Explanation: 342 + 465 = 807.</br>
## <a name="Solution">Solution</a>
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def addTwoNumbers(self, l1, l2):
        """
        :type l1: ListNode
        :type l2: ListNode
        :rtype: ListNode
        """
        list1 = []
        list2 = []
        while l1 != None:
            list1.append(l1.val)
            l1=l1.next

        while l2 != None:
            list2.append(l2.val)
            l2=l2.next
       
        #转换成整数,243->342
        number1=0
        number2=0
        for i in range(0, len(list1)):
            number1 = number1 + pow(10, i)*list1[i]
        for j in range(0, len(list2)):
            number2 = number2 + pow(10, j)*list2[j]
        
        # 相加求和,整数转换成str
        number3 = number1 + number2
        number = str(number3)
        
        
        # 字符串807转换成 7 -> 0 -> 8
        l3 = ListNode(0)
        p = l3
        for i in range(0,len(number)):
            temp = ListNode(0)
            if i == len(number)-1: #最后一个节点
                p.val = number[len(number)-1-i]
                p.next = None
            else: 
                p.val = number[len(number)-1-i]
                p.next = temp
                p = p.next
                
        return l3

```
```
        # 网上的解法
        l3 = ListNode(0) # 始终指向表头
        temp = l3
        number = 0
        while True:            
            if l1 != None:
                number += l1.val
                l1 = l1.next
            if l2!=None:
                number += l2.val
                l2 = l2.next
                
            # 进位
            temp.val = number % 10
            number = number // 10
            
            # 未结束，创建下一个节点，并链接
            if l1 != None or l2 != None :
                temp.next = ListNode(0)
                temp = temp.next
            else:
                break
        return l3
 ```
## <a name="Note">Note</a>
* 我的思路：首先将链表中的数值取出来到list中，再将list中的元素转为整数，相加求和后，最后转为字符串，分别赋值给listnode中的var，下一个元素的地址给listnode中的next</br>
* 最后一步的时候，分开写是因为最后一个节点listnode，如果不单独处理，其next会指向temp，导致输出结果比正确的多一个0
* 别人的解法：边取边加节点
* 注意：py3中，取整是用//，不再是/






