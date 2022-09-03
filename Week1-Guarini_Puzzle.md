# Guarini Puzzle Problem


<img width="723" alt="Screenshot 2022-09-03 at 18 45 29" src="https://user-images.githubusercontent.com/25585589/188266977-0d1cf527-45ec-49c8-88a7-ae77470c4fec.png">
There are 2 white knights and 2 black knights placed on the corners of a 3x3 chessboard.
And we need to find out how can the white knights and black knights exchange their position.

First, we label the chessboard as:

<img width="242" alt="Screenshot 2022-09-03 at 18 54 42" src="https://user-images.githubusercontent.com/25585589/188267267-e4541632-d41d-4324-bd2e-24e1c1c2119f.png">

We do not label the middle point because it is impossible for a knight to move on that position.

<img width="241" alt="Screenshot 2022-09-03 at 18 57 05" src="https://user-images.githubusercontent.com/25585589/188267337-f12d9b8c-527d-44e8-9019-91b19f94b7df.png">
<img width="295" alt="Screenshot 2022-09-03 at 19 01 05" src="https://user-images.githubusercontent.com/25585589/188267448-941b2907-16a8-4c4b-8bb3-4a16a1565dcf.png">
The above is the graph solution.

It is simple to get the solution with the graph. We just need to follow the graph and move the knight.
As 4 knights are at 1, 3, 6, 8, therefore we can only choose these as starting point.

<img width="241" alt="Screenshot 2022-09-03 at 19 31 37" src="https://user-images.githubusercontent.com/25585589/188268443-3ac09081-7591-4fa3-a44b-8dcb7d4c560c.png">

w1, w2 mean white knights
b1, b2 mean black knights

Step (1 as starting point):
```
Round 1

1 -> 5
6 -> 2
8 -> 4
3 -> 7
```
<img width="244" alt="Screenshot 2022-09-03 at 19 32 01" src="https://user-images.githubusercontent.com/25585589/188268448-448cfdc2-bb7f-4b84-91db-01ab05ec0e4a.png">

```
Round 2

5 -> 6
2 -> 8
4 -> 3
7 -> 1
```

<img width="242" alt="Screenshot 2022-09-03 at 19 33 38" src="https://user-images.githubusercontent.com/25585589/188268508-98039c51-1ffe-404d-9695-a15cc108c56a.png">

```
Round 3

6 -> 2
8 -> 4
3 -> 7
1 -> 5
```

<img width="240" alt="Screenshot 2022-09-03 at 19 34 38" src="https://user-images.githubusercontent.com/25585589/188268534-1f8cabfa-184a-4555-adeb-58779f849330.png">

```
Round 4

2 -> 8
4 -> 3
7 -> 1
5 -> 6
```

<img width="242" alt="Screenshot 2022-09-03 at 19 35 21" src="https://user-images.githubusercontent.com/25585589/188268577-4e0104cd-a4f4-4daa-b024-d0f4f9599d88.png">

Done!

Also it can be done in opposite direction.
