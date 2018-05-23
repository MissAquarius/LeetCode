# [Reverse Integer](https://leetcode.com/problems/reverse-integer/description/)

<!-- GFM-TOC -->
* <a href="#Description">Description</a>
* <a href="#Example">Example</a>
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->


## <a name="Description">Description</a>
>Given a 32-bit signed integer, reverse digits of an integer. </br>

## <a name="Example">Example</a>
>Input: 123</br>
Output: 321</br></br>
>Input: -123</br>
Output: -321</br>
note:Assume we are dealing with an environment which could only store integers within the 32-bit signed integer range: [−2^31,  2^31 − 1].  </br>
For the purpose of this problem, assume that your function returns 0 when the reversed integer overflows.</br>
## <a name="Solution">Solution</a>
```python
class Solution(object):
    def reverse(self, x):
        """
        :type x: int
        :rtype: int
        """
        s=''
        # int转成字符串后,反转
        if x >= 0:
            s = str(x)[::-1]
        else:
            s = '-'+str(x)[:0:-1]
            
        # 转整数   
        s2 = int(s)
        # 判断是否溢出
        if s2 > 2**31-1 or s2 < -2 ** 31:
            s2=0
            
        return s2
       
```
## <a name="Note">Note</a>
* py分片的细节：
  * Sequence[startIndex, endIndex, stride]:按步长stride从序列Sequence中取出[indexStart, indexEnd)范围内的元素组成一个新的序列
  * 先看stride的正负,为正表示顺序取出,为负表示逆序.
  * **逆序的时候注意:startIndex所对应的元素必须先于endIndex所对应的元素被访问到,否则,分片操作返回空序列**
  * e.g </br>
      str="0123456789"  </br>
      str[0:4]    # 0123  </br>
      str[-1:4:-1]   # 98765  </br>
* py中求a的幂的方法:
  * a ** b
  * 使用内置的pow函数,pow(a,b),内置的函数把参数作为int
  * 使用math模块的pow函数,模块的函数把参数作为float





