# Move value (aka pseudo-copy)

In order to move a value A to, say, next cell, we need to add 1 A times to the target (initially empty) cell.

It's like sum : we have A, 0 and we want 0, 0+A=A

# Let's start

* Memory: A, 0
* Cursor: on A
* Input: any

# Process

* while A is not null
  * decrease A
  * increase target
* loop

# Code
```
[    while A is not null
  -  decrease A
  >+ increase target
  <  go back to A
]    loop
```

Minified version
```
[->+<]
```

# Final state

* Memory: 0, A
* Cursor: "0" cell
* Input: unchanged
* Output: unchanged
