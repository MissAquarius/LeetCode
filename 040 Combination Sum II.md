# [Combination Sum II](https://leetcode.com/problems/combination-sum-ii/)

<!-- GFM-TOC -->
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->



## <a name="Solution">Solution</a>
```python
class Solution:
    def dfs(self, candidates, target, valuelist, currentindex):
        if target == 0 and valuelist not in self.result:
            return self.result.append(valuelist)
        for i in range(currentindex, len(candidates)):
            if candidates[i] > target:
                break
            else:
                self.dfs(candidates, target - candidates[i], valuelist + [candidates[i]], i+1)
    
    def combinationSum2(self, candidates, target):
        """
        :type candidates: List[int]
        :type target: int
        :rtype: List[List[int]]
        """
        candidates.sort()
        self.result = []
        
        self.dfs(candidates, target, [], 0)
        return self.result
        
 ```
## <a name="Note">Note</a>
* 类似039题combination-sum(https://leetcode.com/problems/combination-sum/)




