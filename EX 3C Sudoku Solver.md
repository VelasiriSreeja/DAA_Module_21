# EX 3C Sudoku Solver
## DATE:29.04.25
## AIM:
To write a python program to find the solution of sudoku puzzle using Backtracking.


## Algorithm
1. Create a 9x9 grid representing the Sudoku puzzle, with 0s representing empty cells
2. Define a recursive function `solve(grid)`:
   a. Find the next empty cell in the grid (where the value is 0).
   b. For each number from 1 to 9, check if placing the number in the current cell is valid:
      - Ensure the number is not already present in the same row, column, or 3x3 subgrid.
   c. If placing a number is valid, assign it to the cell and recursively call `solve(grid)` for the next empty cell.
   d. If the grid is completely filled (no empty cells left), return True (solution found).
   e. If no number is valid, backtrack by resetting the current cell to 0 and trying the next possibility.

3. If a solution is found, print the grid. If no solution exists, return False.

4. Use the function `solve(grid)` to find and display the solution.

## Program:
```
/*
Program to implement to to find the solution of sudoku puzzle using Backtracking.
Developed by: sreeja.v
Register Number: 212222230169
*/
board = [
    [0, 0, 0, 8, 0, 0, 4, 0, 3],
    [2, 0, 0, 0, 0, 4, 8, 9, 0],
    [0, 9, 0, 0, 0, 0, 0, 0, 2],
    [0, 0, 0, 0, 2, 9, 0, 1, 0],
    [0, 0, 0, 0, 0, 0, 0, 0, 0],
    [0, 7, 0, 6, 5, 0, 0, 0, 0],
    [9, 0, 0, 0, 0, 0, 0, 8, 0],
    [0, 6, 2, 7, 0, 0, 0, 0, 1],
    [4, 0, 3, 0, 0, 6, 0, 0, 0]
]

def printBoard():
    for i in range(0, 9):
        for j in range(0, 9):
            print(board[i][j], end=" ")
        print()

def isPossible(row, col, val):
    for j in range(0, 9):
        if board[row][j] == val:
            return False

    for i in range(0, 9):
        if board[i][col] == val:
            return False

    startRow = (row // 3) * 3
    startCol = (col // 3) * 3
    for i in range(0, 3):
        for j in range(0, 3):
            if board[startRow+i][startCol+j] == val:
                return False
    return True
#####################  Add your code here #########################
def isEmpty():
    for r in range(9):
        for c in range(9):
            if board[r][c] == 0:
                return r, c
    return None


def solve():
    #####################  Add your code here #########################
    empty = isEmpty()
    if empty is None:
        printBoard()
        return True

    row, col = empty
    for guess in range(1, 10):
        if isPossible(row, col, guess):
            board[row][col] = guess
            if solve():
                return True
            board[row][col] = 0
    return False
solve()
```

## Output:
![Screenshot 2025-04-29 141625](https://github.com/user-attachments/assets/cf73a3c0-08e2-45c3-8e80-ec8e3597629c)



## Result:
The Sudoku solver program executed successfully and found the solution for the given puzzle.
