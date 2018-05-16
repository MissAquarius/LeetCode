# [Median of Two Sorted Arrays](https://leetcode.com/problems/median-of-two-sorted-arrays/description/)

<!-- GFM-TOC -->
* <a href="#Description">Description</a>
* <a href="#Example">Example</a>
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->

## <a name="Description">Description</a>
>There are two sorted arrays nums1 and nums2 of size m and n respectively.</br>
Find the median of the two sorted arrays. The overall run time complexity should be O(log (m+n)).</br>

## <a name="Example">Example</a>
>Example1:nums1 = [1, 3]</br>
nums2 = [2]</br>
The median is 2.0</br></br></br>
Example2:nums1 = [1, 2]</br>
nums2 = [3, 4]</br>
The median is (2 + 3)/2 = 2.5</br>
## <a name="Solution">Solution</a>
```python
class Solution:
    def findMedianSortedArrays(self, nums1, nums2):
        """
        :type nums1: List[int]
        :type nums2: List[int]
        :rtype: float
        """
        
        # 类似于二路归并排序
        # 分奇数与偶数
        
        m=len(nums1)
        n=len(nums2)
        medianindex=(m+n)//2
        p=0
        q=0
        nums=[]
        
        # m+n为奇数，归并到（m+n）//2的时候，停止
        if((m+n)%2):
            while(p<m and q<n):
                if(nums1[p]<nums2[q]):
                    if(len(nums)==medianindex+1):
                        return float(nums[medianindex])
                    else:
                        nums.append(nums1[p])
                        p += 1
                else:
                    if(len(nums)==medianindex+1):
                        return float(nums[medianindex])
                    else:
                        nums.append(nums2[q])
                        q += 1
            # 退出循环 说明有一个list归并完了,还没找到中位数
            if(p==m): #说明第一路归并完了,第二路直接加进去
                while(q<=n):
                    if(len(nums)==medianindex+1):
                        return float(nums[medianindex])
                    else:
                        nums.append(nums2[q])
                        q += 1
            else:# 说明第二路归并完了，第一路直接加进去
                while(p<=m):
                    if(len(nums)==medianindex+1):
                        return float(nums[medianindex])
                    else:
                        nums.append(nums1[p])
                        p += 1
                
                        
          # m+n为偶数，归并到（m+n）//2的时候，停止
        else:
            while(p<m and q<n):
                if(nums1[p]<nums2[q]):
                    if(len(nums)==medianindex+1):
                        return float((nums[medianindex]+nums[medianindex-1])/2)
                    else:
                        nums.append(nums1[p])
                        p += 1
                else:
                    if(len(nums)==medianindex+1):
                        return float((nums[medianindex]+nums[medianindex-1])/2)
                    else:
                        nums.append(nums2[q])
                        q += 1
            # 退出循环 说明有一个list归并完了,还没找到中位数
            if(p==m): #说明第一路归并完了,第二路直接加进去
                while(q<=n):
                    if(len(nums)==medianindex+1):
                        return float((nums[medianindex]+nums[medianindex-1])/2)
                    else:
                        nums.append(nums2[q])
                        q += 1
            else:# 说明第二路归并完了，第一路直接加进去
                while(p<=m):
                    if(len(nums)==medianindex+1):
                        return float((nums[medianindex]+nums[medianindex-1])/2)
                    else:
                        nums.append(nums1[p])
                        p += 1   
            
        # 网上的方法： 递归(明天再写)
        
 ```
## <a name="Note">Note</a>
* 我的思路：类似于二路归并排序算法;还有就是只用指针游走,这种对边界条件需要仔细把握,没有用
* 别人的解法：递归
* 递归参考资料：
    * http://shmilyaw-hotmail-com.iteye.com/blog/2280941
    * https://www.cnblogs.com/zuoyuan/p/3759682.html







