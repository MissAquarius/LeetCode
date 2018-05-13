# [Two Sum](https://leetcode.com/problems/two-sum/description/)

<!-- GFM-TOC -->
* <a href="#Description">Description</a>
* <a name="Example">Example</a>
* <a name="Solution">Solution</a>
* <a name="Note">Note</a>
<!-- GFM-TOC -->


## <a name="Description">Description</a>
>Given an array of integers, return indices of the two numbers such that they add up to a specific target.</br>
You may assume that each input would have exactly one solution, and you may not use the same element twice.</br>

## <a href="#Example">Example</a>
>Given nums = [2, 7, 11, 15], target = 9</br>
Because nums[0] + nums[1] = 2 + 7 = 9</br>
return [0, 1].</br>

## <a href="#Solution">Solution</a>
```python
# -*- coding: utf-8 -*-
def twoSum(nums, target):
    list = [-1, -1]
    for i in range(0, len(nums)):
        for j in range(i + 1, len(nums)):
            if nums[i] + nums[j] == target:
                list[0] = i
                list[1] = j
                break
    return list


nums = input().split(',')
for i in range(len(nums)):
    nums[i] = int(nums[i])
target = int(input())
print(twoSum(nums, target))
```
## <a href="#Note">Note</a>
py中input()接收的输入均是看做字符串处理，接收完注意类型转换





