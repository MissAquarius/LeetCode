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
class Solution:
    def maxSubArray(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        ## 分治法
        if len(nums) == 0:
            return 0
        return self.divide(nums, 0, len(nums)-1)
    
    def divide(self, nums, left, right):
        
        if left >=  right:
            return nums[right]  ## return nums[left]
        
        middle = (left + right) // 2
        ## 左边
        lmax = self.divide(nums, left, middle - 1)
        
        ## 右边
        rmax = self.divide(nums, middle + 1, right)
        
        ## 中间
        mmax = nums[middle]
        temp = mmax
        
        ## 从中间往左走
        for i in range(middle-1, left-1, -1):
            temp += nums[i]
            if temp > mmax:
                mmax = temp
        temp = mmax  ## 左边最大值
         ## 从中间往右走
        for j in range(middle+1, right+1):
            temp += nums[j]
            if temp > mmax:
                mmax = temp
        
        return max(mmax, lmax, rmax)
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
  * 分治法适用于解决原问题可以分解为若干个规模较小的子问题; 子问题互相独立; 子问题的解合并处理后可得到原问题的解
  * 本题中,首先将数组一分为二,最后求得的最大子串要么全部在数组的左边,要么全部在右边,要么横跨了数组的左右两边.而对于一分为二之后的数组,还可以再继续一分为二,其实相当于子问题的求解.
  * 对于左/右边的数组,直接递归调用函数继续划分即可;对于横跨中间的数组,分别从中间数往左往右查找,找到最大值合并即可.
  * 最后求左边,右边,和中间这三种情况的最大值即可.
* 第二种方法思路:遍历nums,对于每一个数字,判断(之前的sum + 这个数字) 和 (这个数字) 比大小.如果(这个数字) 比 (之前的sum + 这个数字) 大的话,
那么说明不需要再继续加了,直接从这个数字,开始继续.同时记得更新ressum.
* 第三种方法称为:Kadane Algorithm,思路与第二种 差不多.思路是:如果之前的sum 小于0了,就重新计算sum;如果sum不小于0,那么追加元素.这种特殊情况是:
整个nums全是负数,因为重新计算那里将cursum置零了.
* 重要前提是:假设nums[i...j]是最终的最大子数组,那么可以下结论其中任意一段的sum都必将大于0.因为假设nums[i...k]和小于0(k小于j),那么去掉这段,后面的
nums[k..j]和比当前的还大,与当前是最大的矛盾.







