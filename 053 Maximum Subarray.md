# [Maximum Subarray](https://leetcode.com/problems/maximum-subarray/description/)

<!-- GFM-TOC -->
* <a href="#Description">Description</a>
* <a href="#Example">Example</a>
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->


## <a name="Description">Description</a>
>Given an integer array nums, find the contiguous subarray (containing at least one number) 
which has the largest sum and return its sum.</br>

## <a name="Example">Example</a>
>Input: [-2,1,-3,4,-1,2,1,-5,4],</br>
Output: 6</br>
Explanation: [4,-1,2,1] has the largest sum = 6.</br>

## <a name="Solution">Solution</a>
```python
# -*- coding: utf-8 -*-

```
```python
# -*- coding: utf-8 -*-
## O(n)复杂度方法
class Solution:
    def maxSubArray(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
    
        ressum = -2147483647  
        cursum = 0
        
        for num in nums:
            cursum = max(cursum + num, num)
            ressum = max(ressum, cursum)
        return ressum   

```

```python
# -*- coding: utf-8 -*-
## O(n)复杂度方法
class Solution:
    def maxSubArray(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
    
        ressum = -2147483647  
        cursum = 0
        
        if max(nums) < 0:
            return max(nums)
        
        for num in nums:
            if  cursum + num > 0:
                cursum += num
            else:
                cursum = 0
            
            if cursum > ressum:
                ressum = cursum 
        return ressum

```    
## <a name="Note">Note</a>
* 第一种方法:分治法.
* 第二种方法思路:遍历nums,对于每一个数字,判断(之前的sum + 这个数字) 和 (这个数字) 比大小.如果(这个数字) 比 (之前的sum + 这个数字) 大的话,
那么说明不需要再继续加了,直接从这个数字,开始继续.同时记得更新ressum.
* 第三种方法称为:Kadane Algorithm,思路与第二种 差不多.思路是:如果之前的sum 小于0了,就重新计算sum;如果sum不小于0,那么追加元素.这种特殊情况是:
整个nums全是负数,因为重新计算那里将cursum置零了.
* 重要前提是:假设nums[i...j]是最终的最大子数组,那么可以下结论其中任意一段的sum都必将大于0.因为假设nums[i...k]和小于0(k小于j),那么去掉这段,后面的
nums[k..j]和比当前的还大,与当前是最大的矛盾.







