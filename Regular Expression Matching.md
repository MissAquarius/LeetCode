# [Regular Expression Matching](https://leetcode.com/problems/regular-expression-matching/submissions/)

<!-- GFM-TOC -->
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->

## <a name="Solution">Solution</a>
```python
##  递归解法
class Solution:
    def isMatch(self, s, p):
        """
        :type s: str
        :type p: str
        :rtype: bool
        """
        if len(p) == 0:
            return len(s) == 0
        
        if len(p) == 1:
            ## 只有s的长度也为1，且s和p的元素可以匹配上才返回true
            return len(s) == 1 and (s[0] == p[0] or p[0] == '.')
        
        if p[1] != '*':
            ## 第一个元素要匹配上 且 后面的元素都能匹配上 才返回true
            ## 走到这步，p的长度至少是2的，所以存在p[0]，但是s的长度不确定，需要判断一下
            return len(s) > 0 and (s[0] == p[0] or p[0] == '.') and self.isMatch(s[1:], p[1:])
        else:
            ## p[1]为*，循环判断首元素是否匹配，匹配的话，截断s的第一位，继续往后匹配
            while(len(s) > 0 and (s[0] == p[0] or p[0] == '.') ):
                if self.isMatch(s, p[2:]):  
                    return True
                else:
                    s = s[1:]  
                    
        ## 退出循环，说明s和p的第一个元素没有匹配上，此时需要将*前的字符看作出现零次，并且继续匹配
        return self.isMatch(s, p[2:])  ## *前的出现零次     
```
```python

```
## <a name="Note">Note</a>
* [参考链接](https://xfge.github.io/2017/09/03/regular-expression-matching/)
* 动态规划没看懂，待补充
* 其他类似的字符串匹配的题目：
  *[044 Wildcard Matching](https://leetcode.com/problems/wildcard-matching/)
  




