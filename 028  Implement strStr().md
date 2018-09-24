# [Implement strStr()](https://leetcode.com/problems/implement-strstr/description/)

<!-- GFM-TOC -->
* <a href="#Description">Description</a>
* <a href="#Example">Example</a>
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->


## <a name="Description">Description</a>
>Implement strStr().</br>
Return the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.</br>

## <a name="Example">Example</a>
>Input: haystack = "hello", needle = "ll"</br>
Output: 2</br>

>Input: haystack = "aaaaa", needle = "bba"</br>
Output: -1</br>

## <a name="Solution">Solution</a>
```python
# -*- coding: utf-8 -*-
class Solution:
    def strStr(self, haystack, needle):
        """
        :type haystack: str
        :type needle: str
        :rtype: int
        """
        ## 三种特殊情况的处理： 1. needle为空(返回0) 2.haystack为空(返回-1) 3.needel的长度大于haystack的长度(返回-1)
        if len(needle) == 0:
            return 0
        if len(haystack) == 0 or len(needle)>len(haystack) :
            return -1
       
        i = 0
        for i in range (len(haystack)):
            ## 在haystack中找到一个元素i与needle的首元素相同
            if(haystack[i] == needle[0]):
                ## haystack的i+1元素开始与needle第二个元素逐个比较
                k = i+1
                j = 1
                while(j < len(needle) and k < len(haystack) and haystack[k] == needle[j]):  
                    k += 1
                    j += 1 
                    
                ## 退出循环,有两种情况:要么全部匹配完，则直接返回初始位置i即可;要么有不匹配的,则i后移,继续匹配
                if j == len(needle):
                    return i

            ## 提高效率,只要发现剩余待匹配的长度小于needle的长度,直接结束匹配
                if len(haystack)-i < len(needle): 
                    return -1
    
        if i == len(haystack)-1 :  ## 说明匹配到结尾了,还未发现
            return -1
```
```python
   # 根据男朋友的代码改的简单方法
class Solution:
    def strStr(self, haystack, needle):
        """
        :type haystack: str
        :type needle: str
        :rtype: int
        """
        ## 三种特殊情况的处理： 1. needle为空(返回0) 2.haystack为空(返回-1) 3.needel的长度大于haystack的长度(返回-1)
        if len(needle) == 0:
            return 0
        if len(haystack) == 0 or len(needle)>len(haystack) :
            return -1
            
        ## 直接控制i取值范围,注意i+j的用法
        i = 0
        while(i<=len(haystack)-len(needle)):
            j = 0 
            while(j < len(needle)):
                if haystack[i+j] != needle[j]:
                    break
                j += 1
            if j == len(needle):
                return i
            i +=1
        return -1
```
```python
   # 利用py内置函数
     return haystack.find(needle)
```
## <a name="Note">Note</a>
* 注意的几个问题:
  * 三种特殊情况的处理</br>
  * i的取值要在len(haystack)-len(needle)之间
  * 时刻控制index不要越界
* 可以用py内置的字符串查找函数处理
  * find()方法:查找子字符串第一次出现的位置,若找到返回下标值,找不到返回-1
  * index方法:类似字符串的find方法,区别在于查找不到子串,会抛出异常,而不是返回-1
  * rfind()和rindex()方法用法和上面一样,只是从字符串的末尾开始查找







