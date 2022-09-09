# Floyd Warshall Algorithm

**Floyd warshall algorithm** is one of the way to solve shortest path problem but the main idea when using floyd warshall algorithm is dynamic programming.
The biggest differencd between **floyd warshall algorithm** and **dijkstra algorithm** is Floyd's algorithm finds the shortest path between all vertices and Dijkstra's algorithm finds the shortest path between a single vertex and all other vertices. 

When we are finding the shortest path between a single vertex and all other vertices, we will always use **Dijkstra Algorithm** and the main idea is using greedy algorithm. Using **Dijkstra Algorithm**, we need a adjacency matrix to store length and a priority queue to store vertices and other different thing to complete the algorithm to get the shortest path.

Normally, the time complexity of **Dijkstra Algorithm** is O(n^2), but when we need to find the shortest path between all vertices, we have to run n times **Dijkstra Algorithm** to get all the shortest path. And the time complexity will be O(n^3), it is same as **Floyd Warshall Algorithm**.

If we want to optimization our code, we may need to use **Floyd warshall algorithm** when we are finding the shortest path between all vertices. 

Let use this grapth as example:

<img width="300" alt="Screenshot 2022-09-10 at 00 53 43" src="https://user-images.githubusercontent.com/25585589/189401587-acca9579-fd17-40e9-b7a7-7a81149cc98e.png">

Every node only know the weight with direct linked node and it don't know the weight with other node. 
Therefore, we can set a matrix like this:

Adding node A:

| | A | B | C | D |
| - | - | - | - | - |
|A|0|3|∞|5|
|B|2|0|9|4|
|C|2|0|0|8|
|D|∞|∞|2|0|

Then, we keep adding node to try for a shorter path, if there is a shorter path, we will update the path.
We have to run over the whole graph to find out is there a shorter path.

Adding node A:

| | A | B | C | D |
| - | - | - | - | - |
|A|0|3|∞|5|
|B|2|0|∞|4|
|C|1|0|0|4|
|D|∞|2|2|0|


Adding node B:
| | A | B | C | D |
| - | - | - | - | - |
|A|0|3|9|5|
|B|2|0|9|4|
|C|3|1|0|5|
|D|∞|∞|2|0|

Adding node C:
| | A | B | C | D |
| - | - | - | - | - |
|A|0|3|9|5|
|B|2|0|9|4|
|C|3|1|0|5|
|D|5|3|2|0|

Adding node D:
| | A | B | C | D |
| - | - | - | - | - |
|A|0|3|7|5|
|B|2|0|6|4|
|C|3|1|0|5|
|D|5|3|2|0|

Then we get the shortest path between all vertices.
| | A | B | C | D |
| - | - | - | - | - |
|A|0|3|7|5|
|B|2|0|6|4|
|C|3|1|0|5|
|D|5|3|2|0|

Code:

Graph

```python3
INF = 999
nV = 4 //number of vertices
G = [[0, 3, INF, 5],
    [2, 0, INF, 4],
    [INF, 1, 0, INF],
    [INF, INF, 2, 0]]
```

Floyd warshall Algorithm implementation

```python3
def floyd_warshall(G):
    distance = list(map(lambda i: list(map(lambda j: j, i)), G))

    for k in range(nV):
        for i in range(nV):
            for j in range(nV):
                distance[i][j] = min(distance[i][j], distance[i][k] + distance[k][j])
    print_solution(distance)
    
def print_solution(distance):
    for i in range(nV):
        for j in range(nV):
            if(distance[i][j] == INF):
                print("INF", end=" ")
            else:
                print(distance[i][j], end="  ")
        print(" ") 
        
floyd_warshall(G)
```

output:

```
0  3  7  5   
2  0  6  4   
3  1  0  5   
5  3  2  0 
```



