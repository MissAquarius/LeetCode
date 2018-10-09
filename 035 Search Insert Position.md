# [Search Insert Position](https://leetcode.com/problems/search-insert-position/description/)

<!-- GFM-TOC -->
* <a href="#Description">Description</a>
* <a href="#Example">Example</a>
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->


## <a name="Description">Description</a>
>Given a sorted array and a target value, return the index if the target is found.</br>
If not, return the index where it would be if it were inserted in order.</br>
You may assume no duplicates in the array.</br>

## <a name="Example">Example</a>
>Input: [1,3,5,6], 5 </br>
Output: 2</br>

>Input: [1,3,5,6], 2</br>
Output: 1</br>

>Input: [1,3,5,6], 7</br>
Output: 4</br>

>Input: [1,3,5,6], 0</br>
Output: 0</br>
## <a name="Solution">Solution</a>
```python
class Solution:
    def searchInsert(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: int
        """
        if target in nums:
            return nums.index(target)
        else:
            nums.append(target)
            return  (sorted(nums)).index(target)
    
 ```
## <a name="Note">Note</a>
* 用了py自带的方法,传统方法可以设首尾两个指针,与target判断






