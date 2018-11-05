# [Permutations II](https://leetcode.com/problems/permutations-ii/description/)

<!-- GFM-TOC -->
* <a href="#Description">Description</a>
* <a href="#Example">Example</a>
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->


## <a name="Description">Description</a>
>Given a collection of numbers that might contain duplicates, return all possible unique permutations.</br>

## <a name="Example">Example</a>
>Input: [1,1,2]</br>
Output:</br>
[</br>
  [1,1,2],</br>
  [1,2,1],</br>
  [2,1,1]</br>
]</br>
## <a name="Solution">Solution</a>
```python
import copy
class Solution:
    
    def permuteUnique(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """
        result = []
        for i in range(len(nums)):
            ## 把数字加进来
            if i == 0:  ## 第一个元素
                result.append([nums[i]])
                continue
            else:
                for j in range(len(result)):
                    result[j].append(nums[i])
        
            ## 加进来后的数字与前面的每个数字交换位置
            for k in range(len(result)):
                lastindex = len(result[k]) - 1
                target = result[k][lastindex]
                
                m = lastindex-1
                while(m >= 0):
                    newlist = copy.deepcopy(result[k])
                    newlist[lastindex] = newlist[m]
                    newlist[m] = target
                    if newlist not in result:  ## 多加一个判断
                        result.append(newlist)
                    m -= 1

        return result
```
## <a name="Note">Note</a>
* 思路: 与46题类似;只是在46的结果上进行了去重操作
* 全排列问题,相似的题目有:
  * [31. Next Permutation](https://leetcode.com/problems/next-permutation/)</br>
  * [46. Permutations](https://leetcode.com/problems/permutations/description/)</br>
  * [47. Permutations II](https://leetcode.com/problems/permutations-ii/)</br>
  * [60. Permutation Sequence](https://leetcode.com/problems/permutation-sequence/description/)</br>

  





