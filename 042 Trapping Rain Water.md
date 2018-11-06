# [Trapping Rain Water](https://leetcode.com/problems/trapping-rain-water/description/)

<!-- GFM-TOC -->
* <a href="#Description">Description</a>
* <a href="#Example">Example</a>
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->


## <a name="Description">Description</a>
>Given n non-negative integers representing an elevation map where the width of each bar is 1, </br>
compute how much water it is able to trap after raining.备注:点题目链接可以看图</br>

## <a name="Example">Example</a>
>Input: [0,1,0,2,1,0,1,3,2,1,2,1]</br>
Output: 6</br>

## <a name="Solution">Solution</a>
```python
class Solution:
    def trap(self, height):
        """
        :type height: List[int]
        :rtype: int
        """
        ## 首先找到最高的柱子,然后分成左右两半,各自处理
        if len(height) == 0:
            return 0
        
        maxht = max(height)  ## 最高的柱子
        maxix = height.index(maxht)  ## 最高柱子的下标
        result = 0
        
        ## 左半边
        left = height[0] ## 记录左边当前最高柱子的高度
        i = 1
        while(i < maxix):
            if height[i] > left:
                left = height[i]
            else:
                result += (left - height[i] ) * 1
            i += 1
        
        ## 右半边
        right = height[-1] ## 记录右边当前最高柱子的高度
        j = len(height) - 2
        while(j > maxix):
            if height[j] > right:
                right = height[j]
            else:
                result += (right - height[j] ) * 1
            j -= 1
        
        return result
```
## <a name="Note">Note</a>
* 思路: 首先找到list中最高的柱子,然后分成左右两边单独处理.两边的处理方法一致.
* 对于左右两边的处理方法,以左边为例:从左往右,依次遍历,找到当前最高的柱,然后低的填充计算面积即可;要是当前值大于当前最高的,及时更新最高的柱子即可.
* 看图理解的更透彻.


  





