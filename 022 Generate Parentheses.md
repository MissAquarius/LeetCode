# [Generate Parentheses](https://leetcode.com/problems/generate-parentheses/description/)

<!-- GFM-TOC -->
* <a href="#Description">Description</a>
* <a href="#Example">Example</a>
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->


## <a name="Description">Description</a>
>Given n pairs of parentheses, write a function to generate all combinations of well-formed parentheses.</br>


## <a name="Example">Example</a>
>For example, given n = 3, a solution set is:</br>
[</br>
  "((()))",</br>
  "(()())",</br>
  "(())()",</br>
  "()(())",</br>
  "()()()"</br>
]</br>


## <a name="Solution">Solution</a>
```python
# -*- coding: utf-8 -*-
    
class Solution:
    def generateParenthesis(self, n):
        """
        :type n: int
        :rtype: List[str]
        """      
        self.result = []
        self.generate(n, n, '')
        return self.result
  
       
    def generate(self, leftnum, rightnum, s):
    
        if leftnum == 0 and rightnum == 0:
            self.result.append(s)
            
        if leftnum > 0 :
            self.generate(leftnum-1, rightnum, s+'(')
            
        if rightnum > 0 and leftnum < rightnum :
            self.generate(leftnum, rightnum-1, s+')')   

```

## <a name="Note">Note</a>
* 前提:在长度为1-2n的括号序列中,任何一个位置,左边中左括号的个数必然大于或者等于右括号的个数. 
  * 选择:加左括号或者右括号
  * 限制:左括号没有用完,加左括号; 已经加的左括号个数大于右括号个数(即:剩余的左括号个数小于右括号的个数),加右括号
  * 结束条件:左右括号用完
* py中,类里self的用法







