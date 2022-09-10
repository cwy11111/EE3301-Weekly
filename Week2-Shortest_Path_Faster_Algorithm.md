# Shortest Path Faster Algorithm (SPFA)

Shortest Path Faster Algorithm is an improved version of Bellman Ford Algorithm.
SPFA used queue to optimize the algorithm. The time complexity of SPFA is better than Dijkstra Algorithm.

Why SPFA is better than Dijkstra Algorithm?
SPFA can handle negative-weighted graph, Dijkstra Algorithm cannot.
SPFA has better time complexity than Dijkstra Algorithm.

The time complexity of SPFA is O(VE).

Step of SPFA:
1. Create a queue and the initial queue only have the starting point.
2. Creat a matrix to store the shortest path between the starting point and all the vertices. We will set all the value of the matrix as infinity, and the path to the starting point is 0.
3. Start doing relaxation by using the node in queue to find out the shortest path to all vertices. Repeat this until the queue is empty.

Code:

adjacencyList.py
```python3
class Vertex:
    def __init__(self,key):
        self.id = key
        self.connectedTo = {}
 
    def add_neighbor(self, nbr, weight=0):
        self.connectedTo[nbr] = weight
 
    def __str__(self):
        return str(self.id) + ' connectedTo ' + str([x for x in self.connectedTo])
 
    def get_connections(self):
        return self.connectedTo.keys()
 
    def get_id(self):
        return self.id
 
    def get_weight(self, nbr):
        return self.connectedTo[nbr]
 
 
class Graph:
    def __init__(self, num=None):
        self.vertList = {}
        self.numVertices = 0
        if num is not None:
            [self.add_vertex(i+1) for i in range(num)]
 
    def add_vertex(self, key):
        self.numVertices += 1
        v = Vertex(key)
        self.vertList[key] = v
        return v
 
    def get_vertex(self, n):
        if n in self.vertList:
            return self.vertList[n]
        else:
            return None
 
    def __contains__(self, item):
        return item in self.vertList
 
    def add_edge(self, u, v, w = float('inf')):
        if u not in self.vertList:
            self.add_vertex(u)
        if v not in self.vertList:
            self.add_vertex(v)
        self.vertList[u].add_neighbor(self.vertList[v].get_id(), w)
 
    def get_vertices(self):
        return self.vertList.keys()
 
    def __iter__(self):
        return iter(self.vertList.values())
```

Main.py
```python3
import queue
from adjacencyList import Graph
 
 
def spfa(graph, src):
    if graph is None:
        return None
    dis = [float('inf') if i != src else 0 for i in range(graph.numVertices + 1)]
    book = [False for i in range(graph.numVertices + 1)]
    que = queue.Queue()
    que.put(graph.get_vertex(src))
    while not que.empty():
        u = que.get()
        u_id = u.get_id()
        con = [nei for nei in u.get_connections()]
        for c in con:
            if dis[c] > dis[u_id] + u.get_weight(c):
                dis[c] = dis[u_id] + u.get_weight(c)
 
                if not book[c]:
                    que.put(graph.get_vertex(c))
                    book[c] = True
        book[u_id] = False
 
    return dis[1:]
 
 
if __name__ == '__main__':
    graph = Graph(5)
    graph.add_edge(1, 2, 2)
    graph.add_edge(1, 5, 10)
    graph.add_edge(2, 3, 3)
    graph.add_edge(2, 5, 7)
    graph.add_edge(3, 4, 4)
    graph.add_edge(4, 5, 5)
    graph.add_edge(5, 3, 6)
 
    print(spfa(graph, 1))
```

Ref:
https://blog.csdn.net/weixin_40679158/article/details/122167340
