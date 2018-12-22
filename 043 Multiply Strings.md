# [Multiply Strings](https://leetcode.com/problems/multiply-strings/)

<!-- GFM-TOC -->
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->

## <a name="Solution">Solution</a>
```python
class Solution:
    def multiply(self, num1, num2):
        """
        :type num1: str
        :type num2: str
        :rtype: str
        """
        if num1 == '0' or num2 == '0':
            return '0'
        maxlen = len(num1) + len(num2)
        result = [0] * maxlen
        
        ## 下标i + j + 1 = maxlen - 1
        for i in range(len(num1) - 1, -1, -1):
            for j in range(len(num2) - 1, -1, -1):
                result[i + j + 1] += (int(num1[i]) - 0) * (int(num2[j]) - 0)

        ## 处理进位
        temp = 0 ## 初始进位为0
        for k in range(len(result) - 1, -1, -1):
            result[k] += temp
            temp = result[k] // 10  ## 进位的数值
            result[k] -= (temp * 10)
            
        res = ''.join(str(r) for r in result)      ## 注意list转str的方法
        return res.lstrip('0')

 ```
## <a name="Note">Note</a>
* 思路：按照普通乘法列竖式的计算过程首先把每一位相乘的结果存入list，让再处理进位，参考图
* str与list互相转换
  * str转list：直接list(str)即可，如：str1 = '123' 则list(str1) 返回['1', '2', '3']
  * list转str：直接''.join(list)  如：list1 = ['1', '2', '3']，则''.join(list1) 返回'123'
    * 特别注意只有list里面的元素是str形式的才能这样直接join，若是其他类型，先进行类型转换。如：list1 = [1, 2, 3]，则需要''.join(str(l) for l in list1) 
* py中strip函数的用法：用于去除str中首尾指定的字符，默认是空格以及\n \t之类，还可以指定字符或者字符串，若是字符串，只要包含在字符串里的都删除。
如'hi123ih'.strip(hi)返回'123'
* lstrip()和rstrip()是只去除首和尾.




