# [Substring with Concatenation of All Words](https://leetcode.com/problems/substring-with-concatenation-of-all-words/description/)

<!-- GFM-TOC -->
* <a href="#Description">Description</a>
* <a href="#Example">Example</a>
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->


## <a name="Description">Description</a>
>
You are given a string, s, and a list of words, words, that are all of the same length. 
Find all starting indices of substring(s) in s that is a concatenation of each word in words exactly once and without any intervening characters.</br>

## <a name="Example">Example</a>
>Input:</br>
s = "barfoothefoobarman",</br>
words = ["foo","bar"]</br>
Output: [0,9]</br>
Explanation: Substrings starting at index 0 and 9 are "barfoor" and "foobar" respectively.</br>
The output order does not matter, returning [9,0] is fine too.</br>

>Input:</br>
s = "wordgoodstudentgoodword",</br>
words = ["word","student"]</br>
Output: []</br>

## <a name="Solution">Solution</a>
```python
import operator
class Solution:
    def findSubstring(self, s, words):
        """
        :type s: str
        :type words: List[str]
        :rtype: List[int]
        """
        res = []
        ## 利用words中的单词等长的特点,逐个单词遍历
        if len(s) == 0 or len(words) == 0:
            return res

        ## 建立第一个hashmap，存储每个单词出现的次数
        dict1={}
        for word in words:
            if word not in dict1:
                dict1[word] = 1
            else:
                dict1[word] += 1
        ##快速的办法建立第一个hashmap
        ## s = set(words)
        ## for sword in s:
           ## dict1[sword] = words.count(sword)
        ##print(dict1)
        
        ## 对s的子串进行遍历,看是否包含words中的所有单词
        lenwords = len(words)
        lenword = len(words[0])
        lensubstring = lenwords * lenword
        for i in range(0, len(s)-lensubstring+1):
            j = i + lensubstring- 1  ##s[i...j]是待判断的子串
            ## 判断子串是否包含words的全部单词,方法是再建立一个单词的哈希表,与第一个哈希表比较
            ## 逐个单词判断
            start = i
            end = start + lenword - 1
            dict2 ={}
            while(end <= j):
                s1 = s[start:end + 1]

                if s1 not in words:  ## 单词不在words中,直接结束当前子串比较，继续比较下一个子串
                    break
                else:
                    ## 建立第二个哈希表,单词出现的次数不能大于第一个哈希表中对应单词出现的次数
                    if s1 not in dict2: ## 不在直接加入
                        dict2[s1] = 1
                    else:  ## 在的话与第一个哈希表比较次数
                        if dict2[s1] < dict1[s1]:
                            dict2[s1] += 1
                        else:
                            break
                ## 开始比较下一个单词
                start = end + 1
                end = start + lenword - 1
            
            if operator.eq(dict1, dict2) == True:
                res.append(i)
        return res
    
 ```
 ```python
## 待补充其他方法
    
 ```
 
## <a name="Note">Note</a>
* 很显然,菜鸟拿到题目是不会做的,直接上别人的参考资料吧,写的很清楚了.不可否认,程序员虽然把生活过的一团糟,但是他们整理代码以及算法的能力真的是很厉害.面面俱到.
* 参考链接(https://leetcode.windliang.cc/leetCode-30-Substring-with-Concatenation-of-All-Words.html)
* py3中比较字典相等的方法不再是cmp(),而是import operator模块,然后调用operator.eq(dict1, dict2)方法
* 注意方法中注释部分,特别是统计list中出现元素及其个数的方法,笨方法耗时.




