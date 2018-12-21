# [First Missing Positive](https://leetcode.com/problems/first-missing-positive/)

<!-- GFM-TOC -->
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->



## <a name="Solution">Solution</a>
```python
class Solution:
    def firstMissingPositive(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        if nums == None or len(nums) == 0:
            return 1
        
        temp = [0] * len(nums)
        
        for i in range(len(nums)):
            if nums[i] > 0 and nums[i] <= len(nums):
                temp[nums[i] - 1] += 1
        
        for i in range(len(temp)):
            if temp[i] == 0:
                return i + 1
        
        return len(nums) + 1
 
 ```
 ```python

 ```
## <a name="Note">Note</a>
* 思路一待补充
* 



