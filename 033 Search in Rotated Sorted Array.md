# [Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array/description/)

<!-- GFM-TOC -->
* <a href="#Description">Description</a>
* <a href="#Example">Example</a>
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->


## <a name="Description">Description</a>
>Suppose an array sorted in ascending order is rotated at some pivot unknown to you beforehand.</br>
(i.e., [0,1,2,4,5,6,7] might become [4,5,6,7,0,1,2]).</br>
You are given a target value to search. If found in the array return its index, otherwise return -1.</br>
You may assume no duplicate exists in the array.</br>
Your algorithm's runtime complexity must be in the order of O(log n).</br>

## <a name="Example">Example</a>
>Input: nums = [4,5,6,7,0,1,2], target = 0</br>
Output: 4</br>

>Input: nums = [4,5,6,7,0,1,2], target = 3</br>
Output: -1</br>

## <a name="Solution">Solution</a>
```python
class Solution:
    def search(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: int
        """
        
        ## 被人的解法:二分法
        
        if len(nums) == 0:
            return -1
        
        low = 0
        high = len(nums)-1
        
        while(low <= high):
            mid = (low + high) // 2
            if nums[mid] == target:
                return mid
                
            if nums[low] <= nums[mid]:  ## 左边有序
                if target >= nums[low] and target < nums[mid]:
                    high = mid -1
                else:
                    low = mid + 1
            else:         ## 右边有序
                if target >nums[mid] and target <= nums[high]:
                    low = mid + 1
                else:
                    high = mid - 1
        return -1
    
 ```
 ```python
class Solution:
    def search(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: int
        """
        
        ## 二分法
        
        if len(nums) == 0:
            return -1
        
        if len(nums) == 1:
            if nums[0] == target:
                return 0
            else:
                return -1
        
        
        if target > nums[len(nums)-1] and target < nums[0]:
            return -1
        
        if target >= nums[0]:
            i = 0
            while(i+1<len(nums) and nums[i+1] > nums[i] and target != nums[i]):
                i += 1
            if target == nums[i]:
                return i
            else:
                return -1
            
        if target <= nums[len(nums)-1]:
            j = len(nums)-1
            while(j > -1 and nums[j-1] < nums[j] and target != nums[j]):
                j -= 1
            if target == nums[j]:
                return j
            else:
                return -1
    
 ```
 
## <a name="Note">Note</a>
* 自己的思路:将排序后的列表旋转后,左边的数字是从nums[0]逐渐增大(从左到右),右边的数字是从nums[len(nums)-1]逐渐减小(从右到左).所以在左边和右边查找,用后一个数比前一个数大或者小来控制是否将该有序部分遍历完,遍历完还未发现就返回-1
* 别人的解法:二分法.每次从一半开始查找,隔开的两边必定有一边是有序的,在有序的部分可以直接用端值判断是否在范围内:要是在范围内,首尾指针一刀该范围,;要是不在范围内,首尾指针移到另一半的范围,继续折半查找





