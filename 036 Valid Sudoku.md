# [Valid Sudoku](https://leetcode.com/problems/valid-sudoku/description/)

<!-- GFM-TOC -->
* <a href="#Description">Description</a>
* <a href="#Example">Example</a>
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->


## <a name="Description">Description</a>
>Determine if a 9x9 Sudoku board is valid. Only the filled cells need to be validated according to the following rules:</br>
Each row must contain the digits 1-9 without repetition.</br>
Each column must contain the digits 1-9 without repetition.</br>
Each of the 9 3x3 sub-boxes of the grid must contain the digits 1-9 without repetition.</br>

## <a name="Example">Example1</a>
>Input:</br>
[</br>
  ["5","3",".",".","7",".",".",".","."],</br>
  ["6",".",".","1","9","5",".",".","."],</br>
  [".","9","8",".",".",".",".","6","."],</br>
  ["8",".",".",".","6",".",".",".","3"],</br>
  ["4",".",".","8",".","3",".",".","1"],</br>
  ["7",".",".",".","2",".",".",".","6"],</br>
  [".","6",".",".",".",".","2","8","."],</br>
  [".",".",".","4","1","9",".",".","5"],</br>
  [".",".",".",".","8",".",".","7","9"]</br>
]</br>
Output: true</br>


## <a name="Solution">Solution</a>
```python
class Solution:
    def isValidSudoku(self, board):
        """
        :type board: List[List[str]]
        :rtype: bool
        """           
        ## 行
        for i in range(9):
            row = []
            for j in range(9):
                if board[i][j]!='.':
                    if board[i][j] not in row:
                        row.append(board[i][j])
                    else:
                        return False
        
        ## 列
        for j in range(9):
            column = []
            for i in range(9):
                if board[i][j]!='.':
                    if board[i][j] not in column:
                        column.append(board[i][j])
                    else:
                           return False
                    
        ## 子区域
        ## 规律:第i个九宫格的第j个格点,坐标是[i//3*3+j//3*1][i%3*3+j%3*1]
        for i in range(9):
            area = []
            for j in range(9):
                bo = board[(i // 3)*3+(j//3)*1][(i%3)*3+(j%3)*1]
                if bo !='.':
                    if bo not in area:
                        area.append(bo)
                    else:
                        return False
                
        return True

```
## <a name="Note">Note</a>
* 本题是判断给定的9*9的矩阵是否满足数独的条件
 * 数独的规则是:每一行;每一列;每一个九宫格都不能包含重复的数字(0-9),所以本题也就由这个规则去判断
* 判断每一行和每一列的时候,比较简单.难点在于判断每个九宫格,找出九宫格中横坐标与纵坐标之间的关系
* [参考链接](https://www.cnblogs.com/ganganloveu/p/4170632.html)


