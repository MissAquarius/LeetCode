# [Permutations](https://leetcode.com/problems/permutations/description/)

<!-- GFM-TOC -->
* <a href="#Description">Description</a>
* <a href="#Example">Example</a>
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->


## <a name="Description">Description</a>
>Given a collection of distinct integers, return all possible permutations. </br>

## <a name="Example">Example</a>
>Input: [1,2,3]</br>
Output:</br>
[</br>
  [1,2,3],</br>
  [1,3,2],</br>
  [2,1,3],</br>
  [2,3,1],</br>
  [3,1,2],</br>
  [3,2,1]</br>
]</br>
## <a name="Solution">Solution</a>
```python
import copy
class Solution:
    
    def permute(self, nums):
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
                    result.append(newlist)
                    m -= 1
            
        return result
   
```
## <a name="Note">Note</a>
* 思路: 首先将数字加入到list中,然后将新加入的数字与其前面的每个数字交换位置;最后直到所有的数字都加入为止.
* 全排列问题,相似的题目有:
  * [31. Next Permutation](https://leetcode.com/problems/next-permutation/)</br>
  * [46. Permutations](https://leetcode.com/problems/permutations/description/)</br>
  * [47. Permutations II](https://leetcode.com/problems/permutations-ii/)</br>
  * [60. Permutation Sequence](https://leetcode.com/problems/permutation-sequence/description/)</br>
* py中list复制: lista=listb,不是将listb的值拷贝到lista
  * listb = lista[:]
  * listb = list(lista)
  * listb = [i for i in lista]
  * import copy; listb = copy.copy(lista)
  * import copy; listb = copy.deepcopy(lista)
  * 前四种的复制,只要改变listb的值,相应的lista的值也会跟着变化;最后一种不会变化
  





