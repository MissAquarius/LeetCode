# [Integer to Roman](https://leetcode.com/problems/integer-to-roman/description/)

<!-- GFM-TOC -->
* <a href="#Description">Description</a>
* <a href="#Example">Example</a>
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->


## <a name="Description">Description</a>
>Roman numerals are represented by seven different symbols: I, V, X, L, C, D and M.</br>

| Symbol | Value | 
| :------:| :------: | 
| I  | 1 |
| V  | 5 |
| X  | 10 |
| L  | 50 |
| C  | 100 |
| D  | 500 |
| M  | 1000 |

>For example, two is written as II in Roman numeral, just two one's added together. Twelve is written as, XII, which is simply X + II. </br>
The number twenty seven is written as XXVII, which is XX + V + II.</br>
Roman numerals are usually written largest to smallest from left to right. However, the numeral for four is not IIII. </br>
Instead, the number four is written as IV. Because the one is before the five we subtract it making four.</br>
The same principle applies to the number nine, which is written as IX. </br>

>There are six instances where subtraction is used:</br>
I can be placed before V (5) and X (10) to make 4 and 9. </br>
X can be placed before L (50) and C (100) to make 40 and 90. </br>
C can be placed before D (500) and M (1000) to make 400 and 900.</br>
Given an integer, convert it to a roman numeral. Input is guaranteed to be within the range from 1 to 3999.</br>

## <a name="Example">Example</a>
>Input: 3</br>
Output: "III"</br>
Input: 4</br>
Output: "IV"</br>
Input: 9</br>
Output: "IX"</br>
Input: 1994</br>
Output: "MCMXCIV"</br>

## <a name="Solution">Solution</a>
```python
# -*- coding: utf-8 -*-

class Solution:
    def intToRoman(self, num):
        """
        :type num: int
        :rtype: str
        """
        list0 = [['', 'I', 'II', 'III', 'IV', 'V', 'VI', 'VII', 'VIII', 'IX'],
                 ['', 'X', 'XX', 'XXX', 'XL', 'L', 'LX', 'LXX', 'LXXX', 'XC'],
                 ['', 'C', 'CC', 'CCC', 'CD', 'D', 'DC', 'DCC', 'DCCC', 'CM'],
                 ['', 'M', 'MM', 'MMM']     
        ]
        
        result = ''
        
        for i in range(3,-1,-1): 
            index = num // (10 ** i)
            num -= index * (10 **i)
            result += list0[i][index]
        
        return result
                  
```
## <a name="Note">Note</a>
* 固定套路
* py中: 求整(//) ; 幂(**); 求余(%)







