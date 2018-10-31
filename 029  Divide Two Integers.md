# [Divide Two Integers](https://leetcode.com/problems/divide-two-integers/description/)

<!-- GFM-TOC -->
* <a href="#Description">Description</a>
* <a href="#Example">Example</a>
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->


## <a name="Description">Description</a>
>Given two integers dividend and divisor, divide two integers without using multiplication, division and mod operator.</br>
Return the quotient after dividing dividend by divisor.</br>
The integer division should truncate toward zero.</br>

## <a name="Example">Example</a>
>Input: dividend = 10, divisor = 3</br>
Output: 3</br>

>Input: dividend = 7, divisor = -3</br>
Output: -2</br>

## <a name="Solution">Solution</a>
```python
### 超时做法
class Solution(object):
    def divide(self, dividend, divisor):
        """
        :type dividend: int
        :type divisor: int
        :rtype: int
        """
        ## 首先先不管符号,将被除数和除数求绝对值;然后循环判断被除数包含了多少个除数,最后输出个数及判断正负号
        ## [-2147483648~2147483647] 
               
        newdividend = abs(dividend)
        newdivisor = abs(divisor)
        
        i = 0
        while(newdividend >= newdivisor):
            i += 1 
            newdividend-= newdivisor

        ## 符号判断
        if (dividend > 0 and divisor > 0) or (dividend < 0 and divisor < 0):
            return i
        else:
            return -i
    
 ```
 ```python
 class Solution(object):
    def divide(self, dividend, divisor):
        """
        :type dividend: int
        :type divisor: int
        :rtype: int
        """
        ## [−2^31,  2^31 − 1]==[-2147483648~2147483647] 
        
        if dividend == 0:
            return 0
        if dividend == -2147483648 and divisor == -1:
            return 2147483647
        
        a = abs(dividend)
        b = abs(divisor)
        res = 0
        
        while(a >= b):            
            c = b
            count = 1
            while(a >= (c<<1)):
                count = count<<1
                c = c<<1
            ## 计数,进入下个循环
            res += count
            a -= c
        
        if (dividend > 0) ^ (divisor > 0):
            return -res
        else:
            return res
 ``` 
## <a name="Note">Note</a>
* 自己的想法是:判断被除数是否包含除数,包含就计数器加1,最后输出计数器.这样的方法,当被除数与除数之间相差很多时,如被除数很大,除数为1,会超时
* 网上的解法:利用位运算的特性
  ** a<<b的值实际上就是a乘以2的b次方 
  ** a>>b的值实际上就是a整除2的b次方 
* 商的符号判断:
  ** 用异或(^): 相同为0,不同为1
  ** 只有被除数与除数同号时,也即二者均大于0或者均小于0时,也即异或两边的操作数相同时,结果为正
* 位运算这个解法看了好几天才懂,真的是笨到家了.
  ** 第一步:将除数左移1位就是乘以2,一直将除数左移到大于被除数,同时count也要左移相同的次数(参考被除数与除数同时扩大n倍,商不变)
  ** 第二步:每次执行后减去改变后的除数,再重复执行.
  ** 为什么需要第二步？？因为第一步中除数是以倍数增长,比如当除数增长到4倍时,大于被除数了,就要退出循环.如果此时被除数是原始最开始除数的2倍,</br>
  那么就应该开始下次循环.(举例)

