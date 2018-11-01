# [Pow(x, n)](https://leetcode.com/problems/powx-n/description/)

<!-- GFM-TOC -->
* <a href="#Description">Description</a>
* <a href="#Example">Example</a>
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->


## <a name="Description">Description</a>
>Implement pow(x, n), which calculates x raised to the power n (xn).</br>

## <a name="Example">Example</a>
>Input: 2.00000, 10</br>
Output: 1024.00000</br>

>Input: 2.10000, 3</br>
Output: 9.26100</br>

>Input: 2.00000, -2</br>
Output: 0.25000</br>
Explanation: 2-2 = 1/22 = 1/4 = 0.25</br>

## <a name="Solution">Solution</a>
```python
class Solution:
    def poww(self, x, n):
        if n == 1:
            return x
        else:
            half = self.poww(x, n//2)
            if n % 2 == 0:
                return half * half
            else:
                return half * half * x
        
    def myPow(self, x, n):
        """
        :type x: float
        :type n: int
        :rtype: float
        """
        if n == 0:
            return 1
        if n > 0:
            return self.poww(x, n)
        else:
            return 1/self.poww(x, -n)
                             
 ```

## <a name="Note">Note</a>
* Python3.x 中,"/"与"//"差别:
  * '/'  精确除法,返回的是 float. 如:10/5, 结果是 2.0 
  * '//' 去尾整除,返回的是 int.如:5//2, 结果是 2
* 本题如果直接一次乘以x的话,会出现超时错误.因为当n特别大时,需要做n次乘法,运算速度慢.
* 改进的方法是:将n每次除以2,类似于折半相乘.

