# [Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/description/)

<!-- GFM-TOC -->
* <a href="#Description">Description</a>
* <a href="#Example">Example</a>
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->


## <a name="Description">Description</a>
>Given a sorted array nums, remove the duplicates in-place such that each element appear only once and return the new length.</br>
Do not allocate extra space for another array, you must do this by modifying the input array in-place with O(1) extra memory.</br>
Clarification:</br>
Confused why the returned value is an integer but your answer is an array?</br>
Note that the input array is passed in by reference, which means modification to the input array will be known to the caller as well.</br>

## <a name="Example">Example</a>
>Given nums = [1,1,2],</br>
Your function should return length = 2, with the first two elements of nums being 1 and 2 respectively.</br>
It doesn't matter what you leave beyond the returned length.</br>

>Given nums = [0,0,1,1,1,2,2,3,3,4],</br>
Your function should return length = 5, with the first five elements of nums being modified to 0, 1, 2, 3, and 4 respectively.</br>
It doesn't matter what values are set beyond the returned length.</br>


## <a name="Solution">Solution</a>
```python
# -*- coding: utf-8 -*-
class Solution:
    def removeDuplicates(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        ## 特殊情况
        if len(nums) == 0:
            return 0
        ## 设定首次基准元素是nums的第一个元素
        i = 0
        
        for j in range(len(nums)): ## 注意range不要写成(1, len(nums)),当nums只有一个元素的时候会报错,多比较一次即可
            if nums[j] != nums[i]: ## 往后找与基准元素不同的第一个元素
                nums[i+1] = nums[j] ## 不同元素与基准元素右近邻元素交换数值
                i = i + 1  ## 新基准元素
        return i+1   

```

## <a name="Note">Note</a>
* 提交的时候,发现的小问题: 1:没有判断nums为空的特殊情况;  2:最开始range那个地方写的是range(1:len(nums))这样写是错误的,因为len(nums)==1时异常</br>
* 本题注意审题:1:给定的list是有序的,这样不会出现1,2,1,1这样情况; 
2:本题要求在原输入数组上更改,不让开辟新的存储空间,即结果返回lengh,则原数组前length个元素必须是排好序后的不重复元素,后面的元素不作要求
* 解题思路:利用"排好序"这个信息,首先以第一个元素为基准,向后查找第一个不等于该元素的元素,将其与基准元素后面的元素交换数值;
然后基准元素变完第二个元素,依次类推
* range(a, b)表示取[a, b)之间的数,步长为1






