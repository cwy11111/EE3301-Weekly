# Kruskal's Algorithm

Kruskal's Algorithm is an algorithm to find a minimum spanning tree of an undirected edge-weighted graph.
The idea of Kruskal's Algorithm can separate into 3 steps.
1. Starts with an empty tree T
2. Consider edges in increasing order of weight.
3. Case 1: If adding e to T creates a cycle, discard e. or Case 2: Otherwise, insert e = (u, v) into T according to cut lemma.

Case 1:
