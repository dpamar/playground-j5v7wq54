# Copy value 

Copying a value is a destructive operation. The initial value is deleted while 2 copies are created.

Optionally, an extra "Move" operation can be used to move one of the 2 copies at source location, to create a "conservative copy illusion".

# Let's start

* Memory: A, 0, 0
* Cursor: on A
* Input: any

# Process

* while A is not null
  * _invariant: A cell + 1s next cell = A, and 1st next cell = 2nd next cell_
  * decrease A
  * increase 1st next cell
  * increase 2nd next cell
* loop
* _A cell = 0, 1st next cell = A - 0 = A and 2nd next cell = 1st next cell = A_

# Code
```
[    while A is not null
  -  decrease A
  >+ increase 1st next cell
  >+ increase 2nd next cell
  <<  go back to A
]    loop
```

Minified version
```
[->+>+<<]
```

# Final state

* Memory: 0, A, A
* Cursor: "0" cell
* Input: unchanged
* Output: unchanged

# Variant

As explained, we can move the 2nd copy to source location to have A, A, 0 instead of 0, A, A
```
[->+>+<<]    copy value
>>[-<<+>>]<< go to 2nd copy; move it to source location; then go back to source location
```


# Test program
```
,         read a char
[->+>+<<] copy value
>.        go to 1st copy and print
>.        go to 2nd copy and print

```
