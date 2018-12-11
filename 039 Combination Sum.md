# [Combination Sum](https://leetcode.com/problems/combination-sum/description/)

<!-- GFM-TOC -->
* <a href="#Description">Description</a>
* <a href="#Example">Example</a>
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->


## <a name="Description">Description</a>
>Given a set of candidate numbers (candidates) (without duplicates) and a target number (target), </br>
find all unique combinations in candidates where the candidate numbers sums to target.</br>
The same repeated number may be chosen from candidates unlimited number of times.</br>
Note:</br>
All numbers (including target) will be positive integers.</br>
The solution set must not contain duplicate combinations.</br>

## <a name="Example">Example1</a>
>Input: candidates = [2,3,6,7], target = 7,</br>
A solution set is:</br>
[</br>
  [7],</br>
  [2,2,3]</br>
]</br>

## <a name="Example">Example2</a>
>Input: candidates = [2,3,5], target = 8,</br>
A solution set is:</br>
[</br>
  [2,2,2,2],</br>
  [2,3,3],</br>
  [3,5]</br>
]</br>

## <a name="Solution">Solution</a>
```python
class Solution:
    def dfs(self, candidates, target, valuelist, currentindex):
        if target == 0:
            return self.result.append(valuelist)        
        for i in range(currentindex, len(candidates)):
            if candidates[i] > target:
                break
            else:
                self.dfs(candidates, target - candidates[i], valuelist + [candidates[i]], i)  
                
    def combinationSum(self, candidates, target):
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
 ```python
class Solution:
    def dfs(self, candidates, target, valuelist, currentindex):
        if target == 0:
            return self.result.append(valuelist[:])  ## 注意本处写法 
            ## return self.result.append(copy.deepcopy(valuelist))
        for i in range(currentindex, len(candidates)):
            if candidates[i] > target:
                break
            else:
            ## 注意本处写法
                valuelist.append(candidates[i])
                self.dfs(candidates, target - candidates[i], valuelist , i) 
                valuelist.pop()
                
    def combinationSum(self, candidates, target):
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
* 思路:一看到这种返回所有组合的题目,需要想到回溯法.
  * 首先将数组排序,一旦发现当前值大于target,即可停止查找;
  * 对于每个元素,如果小于target,就加入临时列表,并继续添加,因为本题说了一个数字可以重复,因此重新开始添加的下标仍然是当前下标.
  * 递归的终止条件是target==0,表明找到了一个结果,加入结果列表.target缩小,继续上述步骤.
* 两种方法的差别在于递归函数中for循环的写法:
  * 前者是在回溯的时候生成一个新的list,没有改变valuelist的值,因为考虑到将来会回溯回来,保证valuelist值不变;
  * 后者是先将候选值加入valuelist中,回溯的时候再pop出来.因为valuelist的值一直在变,因此append的时候应该是深度拷贝,否则返回的值是错误的.
* 本题将result设置为了全局变量,对于python函数传参是传值还是传引用,一直困惑.以下引用别人的话:
  * python不允许程序员选择采用传值还是传引用(即没有此说法)
  * Python参数传递采用的是“传对象引用”的方式,这种方式相当于传值和传引用的一种综合.
  * 如果函数收到的是一个可变对象（比如字典或者列表）的引用,就能修改对象的原始值－－相当于通过“传引用”来传递对象
  * 如果函数收到的是一个不可变对象（比如数字、字符或者元组）的引用,就不能直接修改原始对象－－相当于通过“传值'来传递对象
* Python 直接赋值/浅拷贝和深度拷贝:
  * 直接赋值:
    * 直接赋值只是传对象的引用,相当于两个变量同时指向一个地方,所以不论这两个变量哪一个改变,他们同时指向的地方都会改变
  * 浅拷贝(copy):
    * 拷贝父对象,不会拷贝对象的内部的子对象
  * 深拷贝(deepcopy): 
    * copy 模块的 deepcopy()方法,完全拷贝了父对象及其子对象
    * list还可以用分片的方式,因为分片操作返回的是一个新的对象
  * 例子:
   ```python
   a = [1, 2, [3, 4], 5]
   
   b = a  
   c = a.copy()
   d = copy.deepcopy(a)
   
   a.append(6)
   a[2].append(0)
   b.append(7)
   
   print(a, b)  ## a=b=[1, 2, [3, 4, 0], 5, 6, 7]
   print(a, c)  ## a=[1, 2, [3, 4, 0], 5, 6, 7]   c=[1, 2, [3, 4, 0], 5] 
   print(a, d)  ## a=[1, 2, [3, 4, 0], 5, 6]   d= [1, 2, [3, 4], 5]
   ```




