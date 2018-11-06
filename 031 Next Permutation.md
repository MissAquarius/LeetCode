# [Next Permutation](https://leetcode.com/problems/next-permutation/description/)

<!-- GFM-TOC -->
* <a href="#Description">Description</a>
* <a href="#Example">Example</a>
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->


## <a name="Description">Description</a>
>Implement next permutation, which rearranges numbers into the lexicographically next greater permutation of numbers.</br>
If such arrangement is not possible, it must rearrange it as the lowest possible order (ie, sorted in ascending order).</br>
The replacement must be in-place and use only constant extra memory.</br>

## <a name="Example">Example</a>
>1,2,3 → 1,3,2</br>
3,2,1 → 1,2,3</br>
1,1,5 → 1,5,1</br>

## <a name="Solution">Solution</a>
```python
class Solution:
    def nextPermutation(self, nums):
        """
        :type nums: List[int]
        :rtype: void Do not return anything, modify nums in-place instead.
        """
        length = len(nums)
        
        i = length - 2
        while(i >= 0):
            if nums[i] < nums[i+1]:
                j = length - 1
                while(nums[j] <= nums[i]):
                    j -= 1
                # 找到需要交换的数
                temp = nums[i]
                nums[i] = nums[j]
                nums[j] = temp 
                nums[i+1:] = nums[-1:i:-1]    ## 重要         
                break
            else:
                i -= 1
         
        if i == -1: ## 表示是最大的数,反转成为最小的数
            nums.reverse()
```
## <a name="Note">Note</a>
* 思路: 以[6, 5, 4, 8, 7, 5, 1]为例,找这个序列的下一个大序列
  * 首先从后往前遍历到不是递减序列[8, 7, 5, 1]的第一个值4
  * 其次将4与递减序列中的与4最接近的数5调换位置,调换完为[6, 5, 5, 8, 7, 4, 1],虽然比上一个数字大,但不是下一个大的
  * 将调换过去的序列[8, 7, 4, 1]反转,变为[1, 5, 7, 8]
  * 因为全排列是从小到大排列的,每一位的数字逐渐增大,因此必然有几位是降序的
* 全排列问题,相似的题目有:
  * [31. Next Permutation](https://leetcode.com/problems/next-permutation/)</br>
  * [46. Permutations](https://leetcode.com/problems/permutations/description/)</br>
  * [47. Permutations II](https://leetcode.com/problems/permutations-ii/)</br>
  * [60. Permutation Sequence](https://leetcode.com/problems/permutation-sequence/description/)</br>
* py中reverse操作,可以将整个列表反转,返回值是None,即反转操作是在原list基础上的
  * eg: lista = [1, 2, 3, 4, 5, 6] lista.reverse();  则lista修改为[6, 5, 4, 3, 2, 1]
* 分片操作也可以实现全反转或者部分反转
* 这题可以扩展成找全排列中前一个最小的数字
  





