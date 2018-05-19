# [Longest Palindromic Substring](https://leetcode.com/problems/longest-palindromic-substring/description/)

<!-- GFM-TOC -->
* <a href="#Description">Description</a>
* <a href="#Example">Example</a>
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->

## <a name="Description">Description</a>
>Given a string s, find the longest palindromic substring in s. You may assume that the maximum length of s is 1000.</br>

## <a name="Example">Example</a>
>Example1:Input: "babad"</br>
Output: "bab"</br>
Note: "aba" is also a valid answer.</br>
Example2:
Input: "cbbd"</br>
Output: "bb"</br>

## <a name="Solution">Solution</a>
```python
import re
class Solution(object):
    def longestPalindrome(self, s):
        """
        :type s: str
        :rtype: str
        """
        # Manacher算法
        # 字符串的首尾和之间添加未曾出现过的字符,使得无论原来是奇串还是偶串，转换后都是奇串
        # 首尾分别加两个不同的字符,保证后面的循环会终止
        
        # 初始化
        #将"babad"变为"*#b#a#b#a#d#^"
        news = "*"+"#"+"#".join(s) + "#"+"^"
        # id是当前右边界最大的回文串的中心,mx是其右边界
        id=0
        mx=0
        p=[0 for i in range(len(news)-1)]
        
        # 开始求数组p[i]
        for i in range(1,len(news)-1):
            # 得到p[i]的一个下界
            if i < mx:
                p[i] = min(p[2*id-i], mx-i)
            else:
                p[i] = 1
            # 继续往mx以后的方向比较,不用担心边界问题，因为首尾加了不同的字符保证一定能够结束
            while(news[i-p[i]]==news[i+p[i]]):
                p[i] += 1 
            # 更新mx，保证mx一定是指向当前所有回文串中右边界最大的那个值,因为mx变了，id也要变
            if mx < i+p[i]:
                id = i
                mx = i+p[i]
        
        # max(p[i])-1是当前的最长回文串的长度
        #首先找到p[i]值最大的下标,是要求的回文子串的中心(圆心)
        center = p.index(max(p[1:]))
        # 半径是p[i]-1,减去1是因为这个p[i]值包括了中心
        radius = p[center]-1
        # 过滤掉添加的字符
        return re.sub('#', '', news[center-radius:center+radius+1])
 ```
## <a name="Note">Note</a>
* Manacher算法,最好情况下,时间复杂度是O(n),用了动态规划的思想
* 算法参考资料:https://segmentfault.com/a/1190000008484167
* py小知识:
  * py可以用正则表达式去除字符串s的某个特定字符'#'(re.sub(pattern, repl, string, count=0, flags=0)):
    import re
    re.sub("#", '', s)
  * py中join方法(str.join(iterable)),可以在字符串中每个字符间添加一个特定的字符,iterable对象可以是string/list/dict等
    list=[1,2,3]
    '+'.join(list)
    print 1+2+3
  * py中,想定义一个有限定长度的list
    list = [i for i in range(length)]
    list = [0 for i in range(length)]
  * 求一个list的最大值及其下标
    最大值 = max(list)
    下标  = list.index(max(list))
    、
    
    






