# [ Remove Element](https://leetcode.com/problems/remove-element/description/)

<!-- GFM-TOC -->
* <a href="#Description">Description</a>
* <a href="#Example">Example</a>
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->


## <a name="Description">Description</a>
>Given an array nums and a value val, remove all instances of that value in-place and return the new length.</br>
Do not allocate extra space for another array, you must do this by modifying the input array in-place with O(1) extra memory.</br>
The order of elements can be changed. It doesn't matter what you leave beyond the new length.</br>
Clarification:</br>
Confused why the returned value is an integer but your answer is an array?</br>
Note that the input array is passed in by reference, which means modification to the input array will be known to the caller as well.</br>


## <a name="Example">Example</a>
>Given nums = [3,2,2,3], val = 3,</br>
Your function should return length = 2, with the first two elements of nums being 2.</br>
It doesn't matter what you leave beyond the returned length.</br>

>Given nums = [0,1,2,2,3,0,4,2], val = 2,</br>
Your function should return length = 5, with the first five elements of nums containing 0, 1, 3, 0, and 4.</br>
Note that the order of those five elements can be arbitrary.</br>
It doesn't matter what values are set beyond the returned length.</br>

## <a name="Solution">Solution</a>
```python
# -*- coding: utf-8 -*-
class Solution:
    def removeElement(self, nums, val):
        """
        :type nums: List[int]
        :type val: int
        :rtype: int
        """
        if len(nums) == 0:
            return 0
        
        j = 0
        for i in range(len(nums)):
            if nums[i] != val:
                nums[j] = nums[i]
                j += 1
        return j
```

## <a name="Note">Note</a>
* 本题类似026题</br>
* 注意该地方返回的是j,因为在上一个判断后j直接加1了</br>







