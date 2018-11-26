# [Longest Valid Parentheses](https://leetcode.com/problems/longest-valid-parentheses/description/)

<!-- GFM-TOC -->
* <a href="#Description">Description</a>
* <a href="#Example">Example</a>
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->


## <a name="Description">Description</a>
>Given a string containing just the characters '(' and ')', find the length of the longest valid (well-formed) parentheses substring.

## <a name="Example">Example1</a>
>Input: "(()"</br>
Output: 2</br>
Explanation: The longest valid parentheses substring is "()"</br>


## <a name="Example">Example2</a>
>Input: ")()())"</br>
Output: 4</br>
Explanation: The longest valid parentheses substring is "()()"</br>

## <a name="Solution">Solution</a>
```python
## 第一种方法
class Solution:
    def longestValidParentheses(self, s):
        """
        :type s: str
        :rtype: int
        """
        l = 0
        res = 0
        stack = []
        
        for i in range(len(s)):
            if s[i] == ')':
                if len(stack) == 0:
                    l = i + 1
                    continue
                else: 
                    stack.pop()
                    if len(stack) == 0:
                        res = max(res, i-l+1)
                    else:
                        res = max(res, i-stack[-1])
            if s[i] =='(':
                stack.append(i)
        
        return res
```
```python
## 动态规划的方法待补充

```
## <a name="Note">Note</a>
* 第一种方法借用堆栈的思路: 
  * 遍历每一个字符,如果是'(',直接入栈;如果是')',则按照步骤2开始
  * 首先判断栈是否为空.为空,则表明当前串匹配结束,需要重新开始下一次的计数(l=i+1),l表示一次合法子串的最左端;不为空,则弹出栈顶元素,栈顶元素与当前右括号是一对
  * 弹完之后,判断栈是否为空.为空则表示,当前串匹配完毕,从l到i之间(包括两端)的子串都是合法的;不为空,表示从栈顶元素的下一个元素到目前i位置的子串都是合法的
* 第二种方法思路
  * test
* 本题拿到后,首先想到的是之前学过的利用堆栈完成字符串匹配问题,不同点在于我把可以匹配的括号下标加入到一个list里面,
  然后妄图在list中寻找最长且数字连续的子串,具体为啥错了我忘记了,现在又觉得这个思路没错TAT,看来以后得及时记录.




