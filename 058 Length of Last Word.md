# [Length of Last Word](https://leetcode.com/problems/length-of-last-word/description/)

<!-- GFM-TOC -->
* <a href="#Description">Description</a>
* <a href="#Example">Example</a>
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->


## <a name="Description">Description</a>
>Given a string s consists of upper/lower-case alphabets and empty space characters ' ', return the length of last word in the string.</br>
If the last word does not exist, return 0.</br>
Note: A word is defined as a character sequence consists of non-space characters only.</br>

## <a name="Example">Example</a>
>Input: "Hello World"</br>
Output: 5</br>

## <a name="Solution">Solution</a>
```python
# -*- coding: utf-8 -*-
class Solution:
    def lengthOfLastWord(self, s):
        """
        :type s: str
        :rtype: int
        """
        count = 0
        i = len(s) - 1
        
        while(i >= 0 and s[i] == ' '):
            i -= 1
        
        ## 退出表示有两种情况
        
        ## i < 0表示s全部都是空格:
        if i < 0:
            return 0
     
        ## s[i]!=' ',开始计数
        while(i >= 0 and s[i] != ' '):
            count += 1
            i -= 1
        return count 

```

```python
# -*- coding: utf-8 -*-
## 利用py的带的方法
class Solution:
    def lengthOfLastWord(self, s):
        """
        :type s: str
        :rtype: int
        """
        ## s.rstrip() 去除右边的空格
        ## .split() 用空格分割字符串,返回的是列表
        ## 取列表中最后一个元素,返回其长度就是最后一个单词的长度
         return len(s.rstrip().split(" ")[-1])
        
```    
## <a name="Note">Note</a>
* 我的方法:从后遍历s,找到非空的元素位置,从该位置开始计数,到出现空格的元素停止计数.
* 简单的利用py带的方法
  * s.strip()方法,去除字符串开头或者结尾的空格;</br> 
    s.lstrip()方法,去除字符串s开头的空格;</br>
    s.rstrip()方法,去除字符串s结尾的空格</br>
  * s.split(str, num)方法: 通过指定分隔符str对字符串进行切片,如果参数 num 有指定值,则仅分隔 num 个子字符串,返回分割后的字符串列表</br>
    str -- 分隔符,默认为所有的空字符,包括空格换行(\n)、制表符(\t)等</br>
    num -- 分割次数</br>
  * join()方法+split()方法,可以去除全部空格: "".join(a.split())先分割,再与空串相加





