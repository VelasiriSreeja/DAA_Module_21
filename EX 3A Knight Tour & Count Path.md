# EX 3A Knight Tour & Count Path
## DATE:29.04.25
## AIM:
To write a python program to find minimum steps to reach to specific cell in minimum moves by knight


## Algorithm
```
1. Define a recursive function `solveKT(board, N, x, y, moveCount, xMove, yMove)`:
   a. If moveCount == N * N (all squares are visited):
      - Return True (all squares visited).
   b. For each move `i` from 0 to 7 (8 possible moves for a knight):
      - Calculate the new position `(new_x, new_y)` using `xMove[i]` and `yMove[i]`.
      - Check if the move is within bounds (0 ≤ new_x < N, 0 ≤ new_y < N) and the square is not yet visited.
      - If valid, mark the square as visited and recursively call `solveKT` with the new position.
      - If the move leads to a solution, return True.
      - If no valid move is found, backtrack: unmark the square and try the next move.

2. Initialize the chessboard as a 2D array of size N x N, with all values set to -1 (unvisited).
3. Define the possible knight's moves as `xMove[] = {2, 1, -1, -2, -2, -1, 1, 2}` and `yMove[] = {1, 2, 2, 1, -1, -2, -2, -1}`.
4. Call `solveKT(board, N, startX, startY, 1, xMove, yMove)` to start from the initial position `(startX, startY)`.
5. Return True if the knight completes the tour, otherwise False.
```
## Program:
```
/*
Program to implement to find minimum steps to reach to specific cell in minimum moves by knight.
Developed by: sreeja.v
Register Number: 212222230169 
*/
KNIGHT_MOVES = [(2, 1), (1, 2), (-1, 2), (-2, 1), (-2, -1), (-1, -2), (1, -2), (2, -1)]
class KnightTour:
    def __init__(self, board_size):
        self.board_size = board_size  # tuple
        self.board = []
        for i in range(board_size[0]):
            temp = []
            for j in range(board_size[1]):
                temp.append(0)
            self.board.append(temp) # empty cell
        self.move = 1

    def print_board(self):
        print('board:')
        for i in range(self.board_size[0]):
            print(self.board[i])

    def warnsdroff(self, start_pos, GUI=False):
        x_pos,y_pos=start_pos
        self.board[x_pos][y_pos]=self.move
        
        if not GUI:
            while self.move<=self.board_size[0]*self.board_size[1]:
                self.move+=1
                next_pos=self.find_next_pos((x_pos,y_pos))
                if next_pos:
                    x_pos,y_pos=next_pos
                    self.board[x_pos][y_pos]=self.move
                else:
                    self.print_board()
                    return self.board
        else:
            if self.move<=self.board_size[0]*self.board_size[1]:
                self.move +=1
                next_pos=self.find_next_pos((x_pos,y_pos))
                return next_pos
                
        

    def find_next_pos(self, current_pos):
        empty_neighbours = self.find_neighbours(current_pos)
        if len(empty_neighbours) == 0:
            return
        least_neighbour = 8
        least_neighbour_pos = ()
        for neighbour in empty_neighbours:
            neighbours_of_neighbour = self.find_neighbours(pos=neighbour)
            if len(neighbours_of_neighbour) <= least_neighbour:
                least_neighbour = len(neighbours_of_neighbour)
                least_neighbour_pos = neighbour
        return least_neighbour_pos

    def find_neighbours(self, pos):
        neighbours = []
        for dx, dy in KNIGHT_MOVES:
            x = pos[0] + dx
            y = pos[1] + dy
            if 0 <= x < self.board_size[0] and 0 <= y < self.board_size[1] and self.board[x][y] == 0:
                neighbours.append((x, y))
        return neighbours

d1=int(input())
d2=int(input())
x=int(input())
y=int(input())
a = KnightTour((d1,d2))
a.warnsdroff((x,y))

```

## Output:
![Screenshot 2025-04-29 140832](https://github.com/user-attachments/assets/d56d17ae-0e6a-4800-b355-a77c817a8d5e)




## Result:
The program executed successfully, and the minimum number of steps for the knight to reach the target was calculated.
