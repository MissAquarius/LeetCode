# [Merge Sorted Array](https://leetcode.com/problems/merge-sorted-array/description/)

<!-- GFM-TOC -->
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->

## <a name="Solution">Solution</a>
```python
class Solution:
    def merge(self, nums1, m, nums2, n):
        """
        :type nums1: List[int]
        :type m: int
        :type nums2: List[int]
        :type n: int
        :rtype: void Do not return anything, modify nums1 in-place instead.
        """
        
        p = m - 1
        q = n - 1
        k = m + n - 1
        while(p >= 0 and q >= 0):
            if nums1[p] > nums2[q]:
                nums1[k] = nums1[p]
                k -= 1
                p -= 1
            else:
                nums1[k] = nums2[q]
                k -= 1
                q -= 1
                
        if p < 0: ## 说明q还有
            while(q >= 0):
                nums1[k] = nums2[q]
                q -= 1
                k -= 1
        ## p还有不用管,因为是归并在nums1中的
 ```
## <a name="Note">Note</a>
* 类似于二路归并排序.从后往前,利用好给的m和n

