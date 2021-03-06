# [Climbing Stairs](https://leetcode.com/problems/climbing-stairs/description/)

<!-- GFM-TOC -->
* <a href="#Description">Description</a>
* <a href="#Example">Example</a>
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->


## <a name="Description">Description</a>
>You are climbing a stair case. It takes n steps to reach to the top.</br>
Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?</br>
Note: Given n will be a positive integer.</br>

## <a name="Example">Example</a>
>Input: 2</br>
Output: 2</br>

>Input: 3</br>
Output: 3</br>

## <a name="Solution">Solution</a>
```python
# -*- coding: utf-8 -*-
class Solution:
    def climbStairs(self, n):
        """
        :type n: int
        :rtype: int
        """
        ## 本质是斐波那契数列,动态规划的方法
        if n == 1:
            return 1
        if n == 2:
            return 2   
        
        res = [0, 1, 2]
        for i in range(3,n+1):
            n = res[i-1] + res[i-2]
            res.append(n)
        
        return res[-1]

``` 
```python
# -*- coding: utf-8 -*-
## 超时的递归
class Solution:
    def climbStairs(self, n):
        """
        :type n: int
        :rtype: int
        """
        ## 本质是斐波那契数列,动态规划的方法
        if n == 1:
            return 1
        if n == 2:
            return 2   
        
        a = self.climbStairs(n - 1)
        b = self.climbStairs(n - 2)
        return a + b
``` 
## <a name="Note">Note</a>
* 动态规划的方法
* 感觉可以用递归方法,待补充吧.超时了,算了,就DP吧.
  






