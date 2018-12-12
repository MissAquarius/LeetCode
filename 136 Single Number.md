# [Single Number](https://leetcode.com/problems/single-number/description/)

<!-- GFM-TOC -->
* <a href="#Description">Description</a>
* <a href="#Example">Example</a>
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->


## <a name="Description">Description</a>
>Given a non-empty array of integers, every element appears twice except for one. Find that single one.</br>
Note:</br>
Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?</br>

## <a name="Example">Example1</a>
>Input: [2,2,1]</br>
Output: 1</br>

## <a name="Example">Example2</a>
>Input: [4,1,2,1,2]
Output: 4

## <a name="Solution">Solution</a>
```python
## 用了额外的空间,计数方法
class Solution:
    def singleNumber(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        dic = {}
        for num in nums:
            if num not in dic:
                dic[num] = 1
            else:
                dic[num] += 1
        
        for key, value  in list(dic.items()):  ## 注意本处写法
            if value == 1:
                return key
 
 ```
 
 ```python
 ## 使用异或操作,不需要额外开辟空间
 class Solution:
    def singleNumber(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        output = 0
        for num in nums:
            output = output ^ num
        
        return output
 ```
 
## <a name="Note">Note</a>
* dict.keys()/dict.values/dict.items()在py3.X中返回的是迭代器,不是之前的列表.为了得到返回值,可以使用list()将其值读到列表里
* dict中的key不可重复,但value可重复.为了得到指定value的key值,需要逐个遍历.
* 不用额外空间的解法:使用py的异或操作(位运算符相同为0,不同为1)
  * 本题用异或,如果相同,返回0;如果不同返回值本身





