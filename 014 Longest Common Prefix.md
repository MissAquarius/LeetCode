# [Longest Common Prefix](https://leetcode.com/problems/longest-common-prefix/description/)

<!-- GFM-TOC -->
* <a href="#Description">Description</a>
* <a href="#Example">Example</a>
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->


## <a name="Description">Description</a>
>Write a function to find the longest common prefix string amongst an array of strings.</br>
If there is no common prefix, return an empty string "".</br>
</br>

## <a name="Example">Example</a>
>Input: ["flower","flow","flight"]</br>
Output: "fl"</br>

>Input: ["dog","racecar","car"]</br>
Output: ""</br>
Explanation: There is no common prefix among the input strings.</br>

## <a name="Solution">Solution</a>
```python
# -*- coding: utf-8 -*-
class Solution:
    def longestCommonPrefix(self, strs):
        """
        :type strs: List[str]
        :rtype: str
        """
        ## 特殊情况,strs是空
        if len(strs) == 0:
            return ""
        
        rstr=""
        for i in range(len(strs[0])):
            for j in range(1,len(strs)):
                if i >= len(strs[j]) or strs[0][i] != strs[j][i]:
                ## 加等号是因为i是从0开始的，当i==len(strs[j])的时候,说明前面已经比较i+1个字母了,而strs[j]的长度只有i,显然无须比较了
                    return rstr
            rstr = rstr+strs[0][i]             
        return rstr
            
```

## <a name="Note">Note</a>
* 思路:拿一个str的元素逐个后面几个元素的逐个字母比较,注意if语句中的等号</br>







