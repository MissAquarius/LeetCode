# [Spiral Matrix](https://leetcode.com/problems/spiral-matrix/)

<!-- GFM-TOC -->
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->


## <a name="Solution">Solution</a>
```python
class Solution:
    def spiralOrder(self, matrix):
        """
        :type matrix: List[List[int]]
        :rtype: List[int]
        """
    
        if matrix == None or len(matrix) == 0:
            return matrix
        
        m = len(matrix)  ## m行
        n = len(matrix[0]) ## n列
        res = []
        left, right, top, bot = 0, n - 1, 0, m - 1
        
        while(left <= right and top <= bot):
            ## 从左到右
            for i in range(left, right + 1):
                res.append(matrix[top][i])
            top += 1
        
                
            ## 从上到下
            for j in range(top, bot + 1):
                res.append(matrix[j][right])
            right -= 1
            
            ## 从右到左
            for m in range(right, left - 1, -1):
                if top <= bot:  ## 防止重复从左到右已经遍历过的
                    res.append(matrix[bot][m])
            bot -= 1
            
            ## 从下到上
            for n in range(bot, top - 1, -1):
                if left <= right:  ## 防止重复从上到下已经遍历过的
                    res.append(matrix[n][left])
            left += 1
            
        return res
 ```
## <a name="Note">Note</a>
* 螺旋遍历矩阵，按照从左到右， 从上到下，从右到左，从下到上的顺序遍历
* 需要注意的细节是：防止重复，后两个遍历前首先判断了四个指针的关系
* range倒序有两种方法：
  * range(10, -1, -1)  ## 10,9 8,7,6,5,4,3,2,1
  * reversed(range(1, 11)  ## 10,9 8,7,6,5,4,3,2,1
* reverse和reversed函数的差别（同sort与sorted）：
  * list.reverse()  ## 在原list上转置
  * reversed(list)  ## 生成一个新的转置后的list，原来的list不变





