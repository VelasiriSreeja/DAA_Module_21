# EX 3B Hamiltonian Circuit Problem
## DATE:29.04.25
## AIM:
To write a python program to check whether Hamiltonian path exits in the given graph.

## Algorithm

1. The Hamiltonian Circuit Problem seeks a path that visits each vertex exactly once and returns to the start.

2. It is solved using backtracking, exploring paths recursively and checking adjacency and unvisited vertices.

3. The algorithm builds the cycle step by step and backtracks when a valid path cannot be formed.

4. The process continues until a complete circuit is formed or all paths are explored.

5. If a circuit is found, return True; otherwise, return False after backtracking.
.   

## Program:

/*
Developed by: sreeja.v
Register Number: 212222230169 
*/
```
class Graph():
    def __init__(self, vertices):
        self.graph = [[0 for column in range(vertices)]
                            for row in range(vertices)]
        self.V = vertices
    def isSafe(self, v, pos, path):
        if self.graph[ path[pos-1] ][v] == 0:
            return False
        for vertex in path:
            if vertex == v:
                return False
 
        return True
    def hamCycleUtil(self, path, pos):
        ######################Add your code here#################################
        if pos==self.V:
            return True
        for v in range(1,self.V):
            if self.isSafe(v,pos,path):
                path[pos]=v
                if self.hamCycleUtil(path,pos+1):
                    return True
                path[pos]==-1
        return False
    def hamCycle(self):
        path = [-1] * self.V
        path[0] = 0
 
        if self.hamCycleUtil(path,1) == False:
            print ("Solution does not exist\n")
            return False
 
        self.printSolution(path)
        return True
 
    def printSolution(self, path):
        print ("Solution Exists: Following",
                 "is one Hamiltonian Cycle")
        for vertex in path:
            print (vertex, end = " ")
        print (path[0], "\n")
g1 = Graph(5)
g1.graph = [ [0, 1, 0, 1, 0], [1, 0, 1, 1, 1],
            [0, 1, 0, 0, 1,],[1, 1, 0, 0, 1],
            [0, 1, 1, 1, 0], ]
g1.hamCycle();

```
## Output:
![Screenshot 2025-04-29 141024](https://github.com/user-attachments/assets/e1398294-54d7-478b-893f-67b313488041)



## Result:
The Hamiltonian path program executed successfully, and it determined whether a Hamiltonian path exists in the given graph.
