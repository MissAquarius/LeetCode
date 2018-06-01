# [ Roman to Integer](https://leetcode.com/problems/roman-to-integer/description/)

<!-- GFM-TOC -->
* <a href="#Description">Description</a>
* <a href="#Example">Example</a>
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->


## <a name="Description">Description</a>
>Roman numerals are represented by seven different symbols: I, V, X, L, C, D and M.</br></br>
For example, two is written as II in Roman numeral, just two one's added together. Twelve is written as, XII, which is simply X + II. </br>
The number twenty seven is written as XXVII, which is XX + V + II.
Roman numerals are usually written largest to smallest from left to right. However, the numeral for four is not IIII. </br>
Instead, the number four is written as IV. Because the one is before the five we subtract it making four. The same principle applies to
the number nine, which is written as IX. There are six instances where subtraction is used:</br>
I can be placed before V (5) and X (10) to make 4 and 9. </br>
X can be placed before L (50) and C (100) to make 40 and 90. </br>
C can be placed before D (500) and M (1000) to make 400 and 900.</br></br>
Given a roman numeral, convert it to an integer. Input is guaranteed to be within the range from 1 to 3999.</br>

## <a name="Example">Example</a>
>Input: "III" </br>
Output: 3</br></br>

Input: "IV"</br>
Output: 4</br></br>

Input: "LVIII"</br>
Output: 58</br></br>


## <a name="Solution">Solution</a>
```python
class Solution:
    def romanToInt(self, s):
        """
        :type s: str
        :rtype: int
        """
        dic = {"I":1, "V":5, "X":10, "L":50, "C":100, "D":500, "M":1000, "IV":4, "IX":9, "XL":40, "XC":90, "CD":400, "CM":900}
        rint = 0
        
        i = 0
        while(i < len(s)):
            # 用i < len(s)-1保证s[i+1]不越界
            if i < len(s)-1 and (s[i]+s[i+1] in dic.keys()):
                rint += dic[s[i]+s[i+1]]
                i += 2
            else:
                rint += dic[s[i]]
                i += 1
        
        return rint
            
            
```
## <a name="Note">Note</a>
* py中判断指定的键是否存在:key in dict.keys(), py3中没有dict.kas_key(key)这种用法</br>
* 取dict某个key对应的value：dict[key]
* 此题比较简单,但是有个问题花了几分钟来找错误,if语句中用到了s[i+1],要防止越界






