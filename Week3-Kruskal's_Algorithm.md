# Kruskal's Algorithm

Kruskal's Algorithm is an algorithm to find a minimum spanning tree of an undirected edge-weighted graph.
The idea of Kruskal's Algorithm can separate into 3 steps.
1. Starts with an empty tree T
2. Consider edges in increasing order of weight.
3. Case 1: If adding e to T creates a cycle, discard e. or Case 2: Otherwise, insert e = (u, v) into T according to cut lemma.

Case 1 (e creates cycle, so don't add e to T):

<img width="284" alt="Screenshot 2022-09-17 at 21 33 28" src="https://user-images.githubusercontent.com/25585589/190859669-208866e1-bb9e-4fda-a1a6-5edc546d31db.png">

Case 2 (e' doesn't create cycle, so add e' to T):

<img width="287" alt="Screenshot 2022-09-17 at 21 34 20" src="https://user-images.githubusercontent.com/25585589/190859696-136e7747-9138-45d7-9290-00cd4f011938.png">

Example:

<img width="464" alt="Screenshot 2022-09-17 at 21 48 55" src="https://user-images.githubusercontent.com/25585589/190860321-068b05b9-8557-45be-9ed1-fb79e54cf7af.png">
<img width="262" alt="Screenshot 2022-09-17 at 21 49 10" src="https://user-images.githubusercontent.com/25585589/190860332-e7934e8a-dfbe-4cb1-a932-ab86aeefd8ad.png">

We will choose the lowest weight edge which is (D, E), and it doesn't have a loop, so we will choose this edge (Green color).
After a few step, our graph will look like this:

<img width="935" alt="Screenshot 2022-09-17 at 21 52 15" src="https://user-images.githubusercontent.com/25585589/190860503-94a7ee16-2856-40c4-8ae3-283bd911413e.png">

The next edge we need to take is (A, C), but if we take this edge it will create a loop. So we will delete it. And for (B, D), (A, F), (A, B), they all have the same problem so we will delete all of them.

<img width="440" alt="Screenshot 2022-09-17 at 21 54 07" src="https://user-images.githubusercontent.com/25585589/190860580-4ab04151-3da6-4490-9e50-d278b4445ccd.png">

And here is our minimum spanning tree.

<img width="449" alt="Screenshot 2022-09-17 at 21 54 28" src="https://user-images.githubusercontent.com/25585589/190860594-8f651569-59ed-4d89-a29a-2065bcd41360.png">

# Pseudo code:

Create-Set(x):
```
Make-Set(x):
x.parent <- x
x.height <- 0
```

Find-Set(x):
```
while x != x.parent do
    x <- x.parent
return x
```

Kruskal’s Algorithm
```
for each vertex 𝑣 ∈ 𝑉
    Make-Set(𝒗)
sort the edges of 𝐺 into increasing order by weight for each edge (𝑢, 𝑣) ∈ 𝐸 taken in the above order
    if Find-Set(𝑢)≠Find-Set(𝑣) then 
        output edge (𝑢,𝑣)
        Union(𝑢, 𝑣)
```
Running time:
O(E log V)

Ref: https://mycollegenotebook.medium.com/kruskal-algorithm-deb0d64ce271
