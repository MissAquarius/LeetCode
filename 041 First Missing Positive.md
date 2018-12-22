# [First Missing Positive](https://leetcode.com/problems/first-missing-positive/)

<!-- GFM-TOC -->
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->



## <a name="Solution">Solution</a>
```python
class Solution:
    def firstMissingPositive(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        if nums == None or len(nums) == 0:
            return 1
        
        temp = [0] * len(nums)
        
        for i in range(len(nums)):
            if nums[i] > 0 and nums[i] <= len(nums):
                temp[nums[i] - 1] += 1
        
        for i in range(len(temp)):
            if temp[i] == 0:
                return i + 1
        
        return len(nums) + 1
 
 ```
 ```python
class Solution:
    def firstMissingPositive(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        if nums == None or len(nums) == 0:
            return 1
        ## 原地排序        
        i = 0
        while(i < len(nums)):
            if nums[i] > 0  and nums[i] <= len(nums) and nums[nums[i] - 1] != nums[i]:
                temp = nums[nums[i] - 1] 
                nums[nums[i] - 1] = nums[i]
                nums[i] = temp
                i -= 1 ## 当前位置换入了新的值，此位置需要重新比较，所以在此将i回退到前一个位置
            i += 1
        
        for j in range(len(nums)):
            if nums[j] != j + 1:
                return j + 1
        return len(nums) + 1
 ```
 ```python
 class Solution:
    def firstMissingPositive(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        if nums == None or len(nums) == 0:
            return 1
        ## 原地排序        
        for i in range(len(nums)):
            while nums[i] > 0  and nums[i] <= len(nums) and nums[nums[i] - 1] != nums[i]:  ## 此位置换入了新值，需要再次判断，因此用的while
                temp = nums[nums[i] - 1] 
                nums[nums[i] - 1] = nums[i]
                nums[i] = temp
        
        for i in range(len(nums)):
            if nums[i] != i + 1:
                return i + 1
        return len(nums) + 1
 ```
## <a name="Note">Note</a>
* 核心思路是：在数组的i位置存放值为i+1的元素，然后遍历数组，第一个没有按照此规则存放的位置，本应该存放的元素就是需要找的。
* 计数排序的思想，利用数组的index来作为数字本身的索引，把正数按照递增顺序依次放到数组中。即让nums[0]=1, nums[1]=2, nums[2]=3, ... , 这样一来，最后如果哪个数组元素违反了nums[i]=i+1即说明i+1就是我们要求的第一个缺失的正数.
* 思路一：另开一个长度为len(nums)的数组，所有元素初始化为0，然后逐个遍历nums数组，将nums[i]放到新数组的nums[i]-1的位置上；最终遍历新数组，第一个值为0的下标+1是需要返回的值。特别注意的是，如果nums的所有元素均加入到新数组中，即新数组没有值为0的元素，说明nums的数字是从1连续递增的，返回长度加1就行（比如这种情况是：nums=[1,2]）
* 思路二：不另外开辟存储空间，直接在原nums上排序。逐个遍历nums的元素，将nums[i]放到nums[i]-1位置上。代码块2和3都是一样的，注意if的i-=1的处理和while的写法



