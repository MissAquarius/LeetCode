# [Find First and Last Position of Element in Sorted Array](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/description/)

<!-- GFM-TOC -->
* <a href="#Description">Description</a>
* <a href="#Example">Example</a>
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->


## <a name="Description">Description</a>
>
Given an array of integers nums sorted in ascending order, find the starting and ending position of a given target value.</br>
Your algorithm's runtime complexity must be in the order of O(log n).</br>
If the target is not found in the array, return [-1, -1].</br>

## <a name="Example">Example</a>
>Input: nums = [5,7,7,8,8,10], target = 8</br>
Output: [3,4].</br>
Input: nums = [5,7,7,8,8,10], target = 6</br>
Output: [-1,-1]</br>

## <a name="Solution">Solution</a>
```python
class Solution:
    def searchRange(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        i = 0
        j = len(nums) - 1
        rlist= [-1, -1]
        while(i <len(nums) ):
            if nums[i]!= target:
                i += 1
            else:
                rlist[0] = i
                break
                
        while(j >= 0 ):
            if nums[j]!= target:
                j -= 1
            else:
                rlist[1] = j
                break 
                
        
        return rlist
    
 ```
## <a name="Note">Note</a>
* 两个指针,从首尾各自遍历,找到就停止






