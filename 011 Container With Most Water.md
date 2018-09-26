# [Container With Most Water](https://leetcode.com/problems/container-with-most-water/description/)

<!-- GFM-TOC -->
* <a href="#Description">Description</a>
* <a href="#Example">Example</a>
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->


## <a name="Description">Description</a>
>Given n non-negative integers a1, a2, ..., an , where each represents a point at coordinate (i, ai). 
n vertical lines are drawn such that the two endpoints of line i is at (i, ai) and (i, 0).
Find two lines, which together with x-axis forms a container, such that the container contains the most water.</br>
Note: You may not slant the container and n is at least 2.</br>

## <a name="Example">Example</a>
>Input: [1,8,6,2,5,4,8,3,7]</br>
Output: 49</br>

## <a name="Solution">Solution</a>
```python
# -*- coding: utf-8 -*-
class Solution:
    def maxArea(self, height):
        """
        :type height: List[int]
        :rtype: int
        """
        ## 首尾指针分别向中间移动
        area = 0
        left = 0
        right = len(height)-1
        
        while(left < right):
            width = right - left
            minheight = min(height[left],height[right])
            if(width * minheight > area):
                area= width * minheight 
            if(height[left] <= height[right]):  ## 谁小谁移
                left += 1
            else:
                right -= 1
        return area
```
```python
# -*- coding: utf-8 -*-
## 超时方法
    def maxArea(self, height):
        """
        :type height: List[int]
        :rtype: int
        """
        area = 0
        for width in range(len(height)):
            i = 0
            j = i + width
            while (j < len(height)):
                length = min(height[i],height[j])
                if (width * length > area):
                    area = width * length
                i += 1
                j += 1
        return area

```
## <a name="Note">Note</a>
* py中min()函数可以求list或者几个数字中的最小值</br>
* 自己的方法:暴力法,从width为1开始试,一直试到len(height)-1为止,而长度就是取每次两端的最小值.会超时.
* 正解:定义首尾指针,首指针右移动,尾指针左移,谁指向的数值小,谁移动.
* 证明方法如下(设原w表示宽度,w= right - left):通俗地说,谁小让谁移动,这样宽度减小,高度还有可能增加;但是如果让大的移动,那么高度不能超过之前小的那边,这样移动的面积比原来还小,是找不到最大值的.


| 情况 | left == right | left < right | left > right |
| :------:| :------: | :------: | :------: |
| left右移 | NewArea与Area关系不确定,需判断 | NewArea与Area关系不确定 | NewArea最大为 (w-1) * right,比原来小  |
| right左移 | NewArea与Area关系不确定,需判断 | NewArea最大为 (w-1) * left,比原来小 | NewArea与Area关系不确定 |






