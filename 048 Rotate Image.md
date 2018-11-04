# [Rotate Image](https://leetcode.com/problems/rotate-image/description/)

<!-- GFM-TOC -->
* <a href="#Description">Description</a>
* <a href="#Example">Example</a>
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->


## <a name="Description">Description</a>
>You are given an n x n 2D matrix representing an image.</br>
Rotate the image by 90 degrees (clockwise).</br>

>Note:</br>
You have to rotate the image in-place, which means you have to modify the input 2D matrix directly. </br>
DO NOT allocate another 2D matrix and do the rotation.</br>


## <a name="Example">Example</a>
>Given input matrix = 
[
  [1,2,3],
  [4,5,6],
  [7,8,9]
],</br>
rotate the input matrix in-place such that it becomes:</br>
[
  [7,4,1],
  [8,5,2],
  [9,6,3]
]</br>

>Given input matrix =
[
  [ 5, 1, 9,11],
  [ 2, 4, 8,10],
  [13, 3, 6, 7],
  [15,14,12,16]
], </br>
rotate the input matrix in-place such that it becomes:</br>
[
  [15,13, 2, 5],
  [14, 3, 4, 1],
  [12, 6, 8, 9],
  [16, 7,10,11]
]

## <a name="Solution">Solution</a>
```python
class Solution:
    def rotate(self, matrix):
        """
        :type matrix: List[List[int]]
        :rtype: void Do not return anything, modify matrix in-place instead.
        """
        n = len(matrix[0])

        ## 首先将矩阵转置
        for i in range(n):
            j = i
            while(j < n):
                temp = matrix[i][j]
                matrix[i][j] = matrix[j][i]
                matrix[j][i] = temp
                j += 1
        
       ## 然后再在每一行内翻转
        for i in range(n):
            low = 0
            high = n-1
            while(low < high):
                temp = matrix[i][low]
                matrix[i][low] = matrix[i][high]
                matrix[i][high] = temp
                low += 1
                high -= 1
            
```

## <a name="Note">Note</a>
* 思路:首先将矩阵转置;然后每一行内元素翻转







