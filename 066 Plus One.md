# [Plus One](https://leetcode.com/problems/plus-one/description/)

<!-- GFM-TOC -->
* <a href="#Description">Description</a>
* <a href="#Example">Example</a>
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->


## <a name="Description">Description</a>
>Given a non-empty array of digits representing a non-negative integer, plus one to the integer.</br>
The digits are stored such that the most significant digit is at the head of the list, and each element </br>
in the array contain a single digit.</br>
You may assume the integer does not contain any leading zero, except the number 0 itself.</br>

## <a name="Example">Example</a>
>Input: [1,2,3]</br>
Output: [1,2,4]</br>
Explanation: The array represents the integer 123.</br>

>Input: [4,3,2,1]</br>
Output: [4,3,2,2]</br>
Explanation: The array represents the integer 4321.</br>

## <a name="Solution">Solution</a>
```python
# -*- coding: utf-8 -*-
## 自己方法
class Solution:
    def plusOne(self, digits):
        """
        :type digits: List[int]
        :rtype: List[int]
        """
        ## list转成int加1
        temp = 0
        for i in range(0, len(digits)):
            temp += pow(10, len(digits)-1-i) * digits[i]
        temp += 1
        string = str(temp)
        
        res=[]
        ## int 转成str,再转成list输出  
        for s in string:
            res.append(int(s))
            
        return res
```

```python
# -*- coding: utf-8 -*-
## 别人的解法
class Solution:
    def plusOne(self, digits):
        """
        :type digits: List[int]
        :rtype: List[int]
        """
        ## 遍历数组的每位,同时处理进位,如果最后还有进位,则在数组最前面在插入1即可
        
        a = 1  
        i = len(digits) - 1
        while(i >= 0):
            temp = digits[i] + a
            digits[i] = temp % 10  ## 留在digits中的数
            a = temp // 10   ## 进位标志
            i -= 1
        
        ## 退出循环,表示digits每一位都处理了,要是a还等于1,则表示每一位都在进位,即每一位都是9
        if a == 1:
            digits.insert(0, 1)
        return digits
        
        

```    
## <a name="Note">Note</a>
* 我自己的方法:将list每一位读出,转成数字;然后将数字加1;最后将数字再转换成list.注意int和list不可直接转换,因为int是不可iterable,可以借助str类型转换
* 别人的方法:不转换成int,在原有list上直接倒序遍历.从最低位开始处理,首先将最低位+1,处理加1后的进位(进位为1,不进位为0).要是处理完最高位,进位符号还是1,
表明整个数组都是9组成的,即每一位都在进位,需要在list首段插入1
* list.insert(index, element) 将element插入到索引为index的地方
  






