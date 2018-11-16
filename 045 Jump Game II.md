# [Jump Game II](https://leetcode.com/problems/jump-game-ii/description/)

<!-- GFM-TOC -->
* <a href="#Description">Description</a>
* <a href="#Example">Example</a>
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->


## <a name="Description">Description</a>
>Given an array of non-negative integers, you are initially positioned at the first index of the array.</br>
Each element in the array represents your maximum jump length at that position.</br>
Your goal is to reach the last index in the minimum number of jumps.</br>

## <a name="Example">Example</a>
>Input: [2,3,1,1,4]</br>
Output: 2</br>
Explanation: The minimum number of jumps to reach the last index is 2.</br>
Jump 1 step from index 0 to 1, then 3 steps to the last index.</br>
Note:You can assume that you can always reach the last index.</br>

## <a name="Solution">Solution</a>
```python
class Solution:
    def jump(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        count = 0
        lastmax = 0
        nextmax = 0
        i = 0
        while (i < len(nums)-1):
            nextmax = max(nextmax, i + nums[i])     ## 记录每个节点可以遍历到的最大值的最大值       
            if i == lastmax:  ## 遍历到上一个最大长度处了,更新最大长度,步数加1
                lastmax = nextmax
                count += 1
            i += 1
        
        return count
       
```
## <a name="Note">Note</a>
* 思路:待补充

  





