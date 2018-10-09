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
        
        ## 二分法
        
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
## <a name="Note">Note</a>
* 自己的思路为什么错,待补充,今天没带草稿纸
* 网上的解法:二分法,明日一并补充吧,稀里糊涂的






