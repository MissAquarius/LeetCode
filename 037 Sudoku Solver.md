# [Sudoku Solver](https://leetcode.com/problems/sudoku-solver/description/)

<!-- GFM-TOC -->
* <a href="#Description">Description</a>
* <a href="#Example">Example</a>
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->


## <a name="Description">Description</a>
>Write a program to solve a Sudoku puzzle by filling the empty cells.</br>
A sudoku solution must satisfy all of the following rules:</br>
Each of the digits 1-9 must occur exactly once in each row.</br>
Each of the digits 1-9 must occur exactly once in each column.</br>
Each of the the digits 1-9 must occur exactly once in each of the 9 3x3 sub-boxes of the grid.</br>
Empty cells are indicated by the character '.'.</br>

## <a name="Example">Example1</a>
>Input:</br>
Output: </br>


## <a name="Solution">Solution</a>
```python
class Solution:
    ## 合法性判断:判断当前的c值是否使得局部有效(局部指的是该行/列/九宫格区域)
    def isValid(self, board, row, col):
        
        c = board[row][col]
        
        ## 行判断
        for j in range(9):
            if j != col and board[row][j]==c:
                return False
        
        ## 列判断,运用了列表解析
        for i in range(9):
            if i!= row and board[i][col] == c:
                return False
        
        ## 九宫格区域判断
        for m in range(row//3*3, row//3*3+3):
            for n in range(col//3*3, col//3*3+3):
                if m!=row and n!=col and board[m][n] == c:
                    return False        
        return True
    
    def solve(self, board):
        for i in range(9):
            for j in range(9):
                if board[i][j] == '.':
                    for c in '123456789':
                        board[i][j] = c
                        if self.isValid(board, i, j) and self.solve(board):
                            return True
                        board[i][j] = '.'                
                    return False

        return True
    
    def solveSudoku(self, board):
        """
        :type board: List[List[str]]
        :rtype: void Do not return anything, modify board in-place instead.
        """ 
        self.solve(board)

```
## <a name="Note">Note</a>
* 待补充
 


