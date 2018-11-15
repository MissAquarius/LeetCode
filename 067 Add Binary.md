# [Add Binary](https://leetcode.com/problems/add-binary/description/)

<!-- GFM-TOC -->
* <a href="#Description">Description</a>
* <a href="#Example">Example</a>
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->


## <a name="Description">Description</a>
>Given two binary strings, return their sum (also a binary string).</br>
The input strings are both non-empty and contains only characters 1 or 0.</br>

## <a name="Example">Example</a>
>Input: a = "11", b = "1"</br>
Output: "100"</br>

>Input: a = "1010", b = "1011"</br>
Output: "10101"</br>

## <a name="Solution">Solution</a>
```python
# -*- coding: utf-8 -*-
class Solution:
    def addBinary(self, a, b):
        """
        :type a: str
        :type b: str
        :rtype: str
        """
        
        flag = 0 ## 标志进位
        res = ""
        ## 首先将a和b的位数补齐,方便相加
        maxlen = max(len(a), len(b))

        if len(a) < maxlen:
            a = a.zfill(maxlen)
        if len(b) < maxlen:
            b = b.zfill(maxlen)
            
        ## 从末位逐位相加,flag标志进位
        for i in range(maxlen-1, -1, -1):
            temp = int(a[i]) + int(b[i]) + flag
            if temp >= 2:  ## 进位
                flag = 1
                temp = temp - 2
            else:  ## 不进位
                flag = 0
            res = str(temp) + res ## 注意顺序
            
        if flag == 1:  ## 退出循环还有进位,则首位补1
            res = '1' + res
        
        return res

```    
## <a name="Note">Note</a>
* 我自己的方法:首先将两个字符串的位数补充完整,方便逐位相加;加的时候,用标志位记录是否出现进位.
* 注意我的方法每次需要在返回的字符串首部插入元素,用的是加法操作.感觉这个加法的顺序也是有关系的.如"aaa" + "bbb" ="aaabbb";"bbb" +"aaa"="bbbaaa"
* str.zfill(width) 将str按照width的宽度右对齐,左边用0填充.注意不是在原str上改变, 返回的是填充后的一个新对象,原有的str不变.
  






