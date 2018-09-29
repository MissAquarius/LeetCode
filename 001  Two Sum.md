# [Add Two Numbers](https://leetcode.com/problems/add-two-numbers/description/)

<!-- GFM-TOC -->
* <a href="#Description">Description</a>
* <a href="#Example">Example</a>
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->


## <a name="Description">Description</a>
>Given an array of integers, return indices of the two numbers such that they add up to a specific target.</br>
You may assume that each input would have exactly one solution, and you may not use the same element twice.</br>

## <a name="Example">Example</a>
>Given nums = [2, 7, 11, 15], target = 9,</br>
Because nums[0] + nums[1] = 2 + 7 = 9,</br>
return [0, 1].</br>

## <a name="Solution">Solution</a>
```python
class Solution(object):
    def twoSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        '''
        # 循环两次
        list = []
        for i in range(0, len(nums)):
            for j in range(i+1, len(nums)):
                if nums[i] + nums[j] == target:
                    list.append(i)
                    list.append(j)
                    break
        return list
       '''
       # 循环一次
        list = []
        for i in range(0,len(nums)):
            number = target - nums[i]
            if number in nums:
                if nums.index(number) != i:
                    list.append(i)
                    list.append(nums.index(number))
                    break
        return list
    
 ```
## <a name="Note">Note</a>
* py中用in/not in判断某个元素是否在list中存在
* 取list中某个element的下标: list.index(element)
* list.append(element) 在list末尾追加元素






