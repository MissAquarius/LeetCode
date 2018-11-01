# [Count and Say](https://leetcode.com/problems/count-and-say/description/)

<!-- GFM-TOC -->
* <a href="#Description">Description</a>
* <a href="#Example">Example</a>
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->


## <a name="Description">Description</a>
>The count-and-say sequence is the sequence of integers with the first five terms as following:</br>
1 is read off as "one 1" or 11.</br>
11 is read off as "two 1s" or 21.</br>
21 is read off as "one 2, then one 1" or 1211.</br>
Given an integer n where 1 ≤ n ≤ 30, generate the nth term of the count-and-say sequence.</br>
Note: Each term of the sequence of integers will be represented as a string.</br>

## <a name="Example">Example</a>
>Input: 1</br>
Output: "1"</br>

>Input: 4</br>
Output: "1211"</br>

## <a name="Solution">Solution</a>
```python
class Solution:
    def countAndSay(self, n):
        """
        :type n: int
        :rtype: str
        """
        s = "1"
        
        for i in range(1, n):
            temp = ""
            j = 0
            while(j < len(s)):
                count = 1
                while( j + 1 < len(s) and s[j] == s[j+1]):
                    count += 1
                    j += 1
                temp = temp + str(count) + s[j]
                j += 1  ## 这个忘记写了
            s = temp
        return s                  
 ```

## <a name="Note">Note</a>
* Python3.x 中 range() 函数返回的结果是一个整数序列的对象,而不是列表类型.因此无论在其他地方改变了i的值,在range中始终i变为之前的下一个元素
* 本题思想:遍历上一个字符串,统计相等字符及其个数,生成新的字符串
* 这个题曾经出现了index out of range的错误,注意下标控制.
 

