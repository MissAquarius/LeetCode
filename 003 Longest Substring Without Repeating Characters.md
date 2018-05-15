# [Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/description/)

<!-- GFM-TOC -->
* <a href="#Description">Description</a>
* <a href="#Example">Example</a>
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->

## <a name="Description">Description</a>
>Given a string, find the length of the longest substring without repeating characters.</br>

## <a name="Example">Example</a>
>Given "abcabcbb", the answer is "abc", which the length is 3.</br>
Given "bbbbb", the answer is "b", with the length of 1.</br>
Given "pwwkew", the answer is "wke", with the length of 3.</br>
Note that the answer must be a substring, "pwke" is a subsequence and not a substring.</br>
## <a name="Solution">Solution</a>
```python
class Solution:
    def lengthOfLongestSubstring(self, s):
        """
        :type s: str
        :rtype: int
         """
         '''我的错误解法
        # str转换为list
        list1 = list(s)
        
        # 对list去重，并保持原顺序
        list2 = list(set(list1))
        list2.sort(key = list1.index)
        
        # 再转为string,s1为子序列
        # 测试样例：dvdf错误
        s1 = ''.join(list2)
        while s1 != None:
            if s1 in s: 
                return len(s1)
            else: 
                if(s1[1:] in s): #去掉头继续匹配
                    s1 = s1[1:]
                else:
                    if(s1[:-1] in s): # 去掉尾
                        s1 = s1[:-1]     
       '''
        # 其他人解法：滑动窗口算法
        l=0
        h=1
        s2 = s[l:h]
        MaxLength= len(s2)
        
        while(h < len(s)):
            if(s2.count(s[h])==0): # 说明未出现，加入窗口，计数改变，h继续向后滑
                s2 += s[h]
                MaxLength = max(MaxLength, len(s2))
                h += 1
            else: # 说明滑动窗口中有该字符，当前字符串已经不是最大的无重复子串，l向后移动
                s2 = s2[1:]
                l += 1
        return MaxLength
 ```
## <a name="Note">Note</a>
* 我的思路：一直想用set方法对list去重，还考虑了去重之后保持原来的list顺序，不知道为啥会那样想，错误的测试样例见注释中
* 别人的解法：利用滑动窗口算法，l和h分别表示窗口的上下界，s2是一个[l,h)的字符串，比较s[h]是否在s2中有，有的话说明与之前的重复，窗口就要缩小，继续比较；
没有的话，说明没有重复，继续向右滑动，同时计数要改变，需要说明的是计数永远取的是当前值与当前滑动窗口中字符数量的最大值。
* 注意：
  * 字符串s追加字符'a'：s+='a'
  * 字符串截取:s[m,n],表示截取s中的[m,n)元素，即：包括m，不包括n,该方法可以用于去掉字符串首(s[1:])尾(s[:-1])
  * list与str互相转换：str转为list比较简单，直接list(str)即可</br>
  反过来会将list的"[" "]" ","等无关字符转为str，因此list转str的方法是str=''.join(list)
  * list可以用set方法去重，但是去重后元素的顺序是随机的，为了在去重后仍然保持原顺序，
  可以去重后排序：list2=list(set(list1)),list2.sort(key=list1.index)
  * 可以用in/not in 判断元素是否在list中存在(第一题已总结)






