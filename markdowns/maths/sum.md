# Sum numbers

As you probably already noticed, there is no "sum 2 variables" in BF. Variables actually don't exist either :)

The `+` command even does not "add" values : it simply increments current cell, so does the `-` command that decrements current cell.

In order to compute A+B, we have to add 1 to A, B times

# Let's start

* Memory: A, B
* Cursor: on B
* Input: any

# Process

* while B is not null
  * decrease B
  * increase A
* loop

# Code
```
[    while B is not null
  -  decrease B
  <+ go to A and increase
  >  go back to B
]    loop
```

Minified version
```
[-<+>]
```

# Final state

* Memory: A+B, 0
* Cursor: "0" cell
* Input: unchanged
* Output: unchanged
