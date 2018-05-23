# [ZigZag Conversion](https://leetcode.com/problems/zigzag-conversion/description/)

<!-- GFM-TOC -->
* <a href="#Description">Description</a>
* <a href="#Example">Example</a>
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->


## <a name="Description">Description</a>
>The string "PAYPALISHIRING" is written in a zigzag pattern on a given number of rows like this: </br>
(you may want to display this pattern in a fixed font for better legibility)</br>
P   A   H   N </br>
A P L S I I G </br>
Y   I   R </br>
And then read line by line: "PAHNAPLSIIGYIR"</br>

## <a name="Example">Example</a>
>Input: s = "PAYPALISHIRING", numRows = 3 </br>
Output: "PAHNAPLSIIGYIR"</br>

## <a name="Solution">Solution</a>
```python
class Solution(object):
    def convert(self, s, numRows):
        """
        :type s: str
        :type numRows: int
        :rtype: str
        """
        # 一行的时候单独处理
        if numRows == 1:
            return s
        else:
            cycle = 2 * numRows - 2
            rstr=''
            # 逐行处理
            for i in range(0, numRows):
                j = i # 每一个循环内处理,第一个循环中j与i同
                while(j < len(s)):
                    rstr += s[j]
                    secondJ = j + 2 *(numRows - 1- i )
                    # 要判断三种特殊情况:首行没有第二个元素;尾行也没有第二个元素;最后一个循环可能不满,要判断secondJ是否溢出
                    if i!= 0 and i!= numRows-1 and secondJ<len(s):
                        rstr += s[secondJ]
                     # 继续下一个循环
                    j += cycle
            return rstr
       
```
## <a name="Note">Note</a>
* 找规律的题目,写出下标找好对应关系即可;一行的时候单独处理,否则case不过</br>
* range()函数用法:如range(0,10,2),表示取[0,2,4,6,8],第三个参数表示步长(貌似这三个参数不能是变量)
* py中逻辑运算符:没有&&,而是and;相应地,||是or






