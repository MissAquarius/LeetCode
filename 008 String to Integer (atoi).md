# [String to Integer (atoi)](https://leetcode.com/problems/string-to-integer-atoi/description/)

<!-- GFM-TOC -->
* <a href="#Description">Description</a>
* <a href="#Example">Example</a>
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->


## <a name="Description">Description</a>
>Implement atoi which converts a string to an integer.</br>The function first discards as many whitespace characters as necessary until the first non-whitespace character is found. </br>
Then, starting from this character, takes an optional initial plus or minus sign followed by as many numerical digits as possible,and interprets them as a numerical value.</br></br>
The string can contain additional characters after those that form the integral number,which are ignored and have no effect on the behavior of this function.</br></br>
If the first sequence of non-whitespace characters in str is not a valid integral number, or if no such sequence exists because</br> either str is empty or it contains only whitespace characters, no conversion is performed.</br></br>
If no valid conversion could be performed, a zero value is returned. </br>

## <a name="Example">Example</a>
>Input: "42"</br>
Output: 42</br></br>
>Input: "   -42"
Output: -42</br></br>
>Input: "words and 987"</br>
Output: 0</br></br>
>Input: "4193 with words" </br>
Output: 4193</br></br>
note:Only the space character ' ' is considered as whitespace character.
Assume we are dealing with an environment which could only store integers within the 32-bit signed integer range: [−231,  231 − 1].</br> 
If the numerical value is out of the range of representable values, INT_MAX (231 − 1) or INT_MIN (−231) is returned.</br>
## <a name="Solution">Solution</a>
```python
class Solution(object):
    def myAtoi(self, str):
        """
        :type str: str
        :rtype: int
        """
        # 首先找第一个非空字符，若不是-+或者数字，返回0
        if str == "":
            return 0
        else:
            str2 = str.lstrip()
            if str2 == "":
                return 0
            else:
                rstr=''
                if str2[0]!='-' and str2[0]!='+' and str2[0].isdigit()== False:
                    return 0
                else:
                    rstr += str2[0]   # 第一个先加进去，有可能加进去的是符号，之后单独处理
                    for i in range(1, len(str2)):
                        if str2[i].isdigit()==False:
                            break
                        else:
                            rstr += str2[i]
                    # 单独处理符号后面不是数字的情况，即rstr只有一个符号
                    if rstr =="-" or rstr == "+":
                        return 0
            
                    # 判断是否溢出
                    rint = int(rstr)
                    if rint > 2** 31-1:
                        rint = 2** 31-1
                    if rint < -2** 31:
                        rint = -2** 31
            
                    return rint
       
```
## <a name="Note">Note</a>
* 我的思路: 首先去掉str前面的空字符(有两种特殊情况:str==None 或者 str去除后是None,两种情况都是直接返回0):</br>
           然后拿到第一个非空字符,判断是否是正负号或者数字,不是直接返回0,是的话先加进去,注意此处也有特殊情况比如"-w"
           最后,从改点遍历,遇到第一个非数字字符的时候停止,返回的时候注意判断是否溢出
* py去除str前后的空格方法:</br>
  str.strip() # 去除str前后的空格 </br>
  str.lstrip() # 去除str前(左)的空格 </br>
  str.rstrip() # 去除str后(右)的空格 </br>
* py判断一个字符s或者字符串str是否是数字/字母: 以字符s为例</br>
  s.isdigit() # 是否是数字 </br>
  s.isalpha() # 是否是字母 </br>
  





