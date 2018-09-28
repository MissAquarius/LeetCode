# [3Sum Closest](https://leetcode.com/problems/3sum-closest/description/)

<!-- GFM-TOC -->
* <a href="#Description">Description</a>
* <a href="#Example">Example</a>
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->


## <a name="Description">Description</a>
>Given an array nums of n integers and an integer target, find three integers in nums such that the sum is closest to target. </br>
Return the sum of the three integers. You may assume that each input would have exactly one solution.</br>

## <a name="Example">Example</a>
>
Given array nums = [-1, 2, 1, -4], and target = 1.</br>
The sum that is closest to the target is 2. (-1 + 2 + 1 = 2).]</br>
## <a name="Solution">Solution</a>
```python
# -*- coding: utf-8 -*-
class Solution:
    def threeSumClosest(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: int
        """
        nums.sort()
        
        ## 记录最小的差值
        minn = 10000
        if len(nums) == 3:
            return nums[0] + nums[1] + nums[2]
        
        for i in range(0,len(nums)-2):
            j = i + 1
            k = len(nums)-1
           
            while(j < k):
                num = nums[i] + nums[j] + nums[k]
                if num - target == 0:  ## [1,1,1,1] target =3
                    return target
                if abs(num - target) < minn:
                    minn = abs(num - target) 
                    rnum = num
                if num < target:
                    j += 1
                if num > target:
                    k -= 1
        return rnum
            
```
## <a name="Note">Note</a>
* 与015题比较像
* py中求绝对值abs()





