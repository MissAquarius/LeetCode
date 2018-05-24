# [Palindrome Number](https://leetcode.com/problems/palindrome-number/description/)

<!-- GFM-TOC -->
* <a href="#Description">Description</a>
* <a href="#Example">Example</a>
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->


## <a name="Description">Description</a>
>Determine whether an integer is a palindrome. An integer is a palindrome when it reads the same backward as forward. </br>

## <a name="Example">Example</a>
>Input: 121</br>
Output: true</br></br>
>Input: -121</br>
Output: false</br></br>

## <a name="Solution">Solution</a>
```python
class Solution(object):
    def isPalindrome(self, x):
        """
        :type x: int
        :rtype: bool
        """
        str2 = str(x)
        i=0
        j=len(str2)-1
        
        while(i < j):
            if str2[i] == str2[j]:
                i += 1
                j -= 1
            else:
                return False
        return True
       
```
## <a name="Note">Note</a>
* 常规题

  





