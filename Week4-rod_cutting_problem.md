# The Rod Cutting Problem

Given a rod of length n and prices pi for i = 1, ...,n , where pi is the price of a rod o f length i. Find a way to cut the rod  to maximize total revenue.
| length i  | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10|
| -| -|-|-|-|-|-|-|-|-|-|
| price pi  | 1 | 5 | 8 | 9 | 10 | 17 | 17 | 20 | 24 | 30|

First, we let rn be the maximum revenue obtainable from cutting a rod of length n.

Step:
1. rn = max {pn, p1 + rn-1, p2 + rn-2, ... pn-1 + r1}, r1 = p1
  - pn if we do npt cut at all
  - p1 + rm-1 if the first piece has length 1
  - p2 + rn-2 if the first piece has length 2
2. Solve the problem for rod lenght 1,2,...,n.

Basic solution
``` 
let r[]0,...,n] be a new array
r[0] <- 0
for j <- 1 to n
  q <- -∞
  for i <- 1 to j
    q <- max(q, p[i] + r[j-i])
    
  r[j] <- q
return r[n]
```
Result
|i | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10|
| -| -|-|-|-|-|-|-|-|-|-|-|
|p[i] |0| 1 | 5 | 8 | 9 | 10 | 17 | 17 | 20 | 24 | 30|
|r[i] |0| 1 | 5 | 8 | 10 | 13 | 17 | 18 | 22 | 25 | 30|

Added Optimal decision for each subproblem in s[j]
```
let 𝑟[0 . . 𝑛] and 𝑠[0 . . 𝑛] be new arrays
𝑟 0 ← 0
for 𝑗 ← 1 to 𝑛
  𝑞 ← −∞
  for 𝑖 ← 1 to 𝑗
    if 𝑞 < 𝑝[𝑖] + 𝑟[𝑗 − 𝑖] then 
      𝑞 ← 𝑝[𝑖] + 𝑟[𝑗 − 𝑖] 
      𝑠 𝑗 ← 𝑖 
  𝑟 𝑗 ← 𝑞
𝑗 = 𝑛
while 𝑗 > 0 do
  print 𝑠[𝑗]
  𝑗 ← 𝑗 − 𝑠[𝑗]
```

Result
|i | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10|
| -| -|-|-|-|-|-|-|-|-|-|-|
|p[i] |0| 1 | 5 | 8 | 9 | 10 | 17 | 17 | 20 | 24 | 30|
|r[i] |0| 1 | 5 | 8 | 10 | 13 | 17 | 18 | 22 | 25 | 30|
|s[i] |0| 1 | 2 |3 | 2 | 2 |6 | 1 | 2 |3 | 10|

Therefore, the solution is n = 9
j = 9, s[j] = 3
j = 9 - 3 = 6, s[j] = 6
So cut 9 into {3, 6}
