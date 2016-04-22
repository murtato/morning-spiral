# Node Lab - The Spiral Of Doom

![](https://i.ytimg.com/vi/0lkjoTh1Gpk/maxresdefault.jpg)

In this lab we will use node modules to solve a somewhat challenging computer science problem. We're doing it as a team project -- a contest... and a race.

So here's the problem:

Given a number n, print out a _n_ x _n_ grid of the numbers 1 to _n*n_ ordered clockwise as a spiral with 1 at the center

For example, spiral(3) would print out:

```
7 8 9
6 1 2
5 4 3
```

spiral(5) prints out

```
21 22 23 24 25
20 7  8  9  10
19 6  1  2  11
18 5  4  3  12
17 16 15 14 13
```

---

The Algorithm

Writing spiral is NOT easy.

The crucial insight in solving this problem is when we see that each spiral contains spiral(n-1). In fact to get the "next spiral" we:

Walk down (on the right side) and left (on the bottom) if N is even

Walk up (on the left side) and right (on the top) if N is odd

To Solve This Problem, we simply start with a two dimensional array of:

```
[[1]]
```

Now we need four functions:

---

walkDown(spiralArray, n)

and returns 3

```
walkDown([[[7 8 9]
			 [6 1 2]
			 [5 4 3]], 10)
```
		 
sets spiral to

```
[[7 8 9 10]
 [6 1 2 11]
 [5 4 3 12]]
```

and returns 13

---

walkLeft(spiralArray, n)

```
walkLeft([[1 2], 3)
```

sets spiral to

```
[[1 2]
 [4 3]]
```

and returns 5

walkUp(spiralArray, n)

```
walkUp([[1 2]
        [4 3]], 5)
```

sets spiralArray to

```
[[6 1 2]
 [5 4 3]]
```

and returns 7

---

walkRight(spiralArray, n)

```

walkRight([[6 1 2]
			 [5 4 3], 7)
```

sets spiralArray to

```
[[7 8 9]
 [6 1 2]
 [5 4 3]]
```

and returns 10

---

Using these for functions the algorithm can be written as (pseudocode):


```
spiral(n)
  if (n == 1)
    [[1]]
  else 
    spiralArray = spiral(n-1)
    start = (n-1)*(n-1) + 1
    if n % 2 == 0
       start = walkDown(spiralArray, start)
       walkLeft(spiralArray, start)
    else
       start = walkUp(spiralArray, start)
       walkRight(spiralArray, start)
    return spiralArray
```

Finally we need to produce a nice output

```
printArray(spiralArray)
```

Outputs the array in evenly spaced rows and columns.# morning-spiral
