# Breadth-first search(BFS)

Breadth-first search is an algorithm for searching a graph. There are two important things in BFS.
Breadth means the algorithm will work on horizontally then vertically.
We need to use queue, which is the first-in-first-out method, to store vertices.

We usually use this algorithm to solve shortest path problems like starting from a point to an endpoint and we need to find the shortest path between two point.

Step on BFS:
1. Create an empty queue to store nodes and an empty list to store visited nodes.
2. Push starting node and neighbour node into queue and list.
3. Pop the first node from the queue and push all its neighbour nodes into the queue.
4. If the neighbour nodes not in the visited nodes list, append the neighbour nodes into the queue and visit list.
5. Keep repeating step 3 and step 4 until the queue is empty.


<img width="543" alt="Screenshot 2022-09-03 at 03 22 38" src="https://user-images.githubusercontent.com/25585589/188223126-95e18481-5c71-4101-9e2a-1f2cd08257d8.png">
The graph can coded as below.

```python3
graph = {
    'A' : ['B','C','D'],
    'B' : ['A','E'],
    'C' : ['A','D','F','G'],
    'D' : ['A','C','G'],
    'E' : ['B', 'F'],
    'F' : ['C','E', 'H'],
    'G' : ['C','D'],
    'H' : ['F']
}
```
The queue will look like this if we choose C as our starting point:
```
1. [C] //Append C into queue
  visted = []
2. [A, D, F, G] //pop C, append C into visted and push all its neighbour nodes into queue
  visted = [C]
3. [D, F, G, B] //pop A, append A into visted and push all its neighbour nodes into queue
  visted = [C, A]
4. [F, G, B] //pop D, append D into visted and push all its neighbour nodes into queue
  visted = [C, A, D]
5. [G, B, E, H] //pop F, append F into visted and push all its neighbour nodes into queue
  visted = [C, A, D, F]
6. [B, E, H] //pop G, append G into visted
  visted = [C, A, D, F, G]
7. [E, H] //pop B, append B into visted
  visted = [C, A, D, F, G, B]
8. [H] //pop E, append E into visted
  visted = [C, A, D, F, G, B, E]
9.[] //pop H, append H into visted
  visted = [C, A, D, F, G, B, E, H]
```
The above process can coded as:

```python3
def BFS(start,graph):
    queue =[]
    visit = []
    queue.append(start)
    visit.append(start)
    while queue:
        node = queue.pop(0)
        nodes = graph[node]
        for i in nodes:
            if i not in visit:
                queue.append(i)
                visit.append(i)
        print(node,end='\t')
        
```
```python3
BFS('C', graph)
```
The result is:
C       A       D       F       G       B       E       H

This algorithm can find out all node in a graph.

If we want to find the shorest path between two point in a graph, we can use the same method with some changes.
```python3
def BFS2(start,end,graph):
    queue =[]
    visit = []
    queue.append(start)

    if start == end:
        print("Same Node")
        return 

    while queue:
        path = queue.pop(0)
        nodes = path[-1]

        if nodes not in visit:
            neighbours = graph[nodes]

            for neighbour in neighbours:
                new_path = list(path)
                new_path.append(neighbour)
                queue.append(new_path)

                if neighbour == end:
                    print("Shortest path = ", *new_path)
                    return
            visit.append(nodes)
```
```python3
BFS2('A', 'H', graph)
```
The result is:
Shortest path =  A C F H

Advantage of BFS:
1. It can always finds optimal solutions.
Disadvantage of BFS:
1. All of the connected vertices must be stored in memory. So consumes more memory

Ref:
Breadth-first search in 4 minutes
https://www.youtube.com/watch?v=HZ5YTanv5QE&ab_channel=MichaelSambol

Building an undirected graph and finding shortest path using Dictionaries in Python
https://www.geeksforgeeks.org/building-an-undirected-graph-and-finding-shortest-path-using-dictionaries-in-python/

What are the advantages and disadvantages of DFS and BFS?
https://www.quora.com/What-are-the-advantages-and-disadvantages-of-DFS-and-BFS

