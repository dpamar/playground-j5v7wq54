# Evaluate Not() function

If we say that 0 is false, and any other value is true, here is a way to evaluate not(A) from a value A.

Detailled specification is : if A == 0, then A := 1 else A := 0

This allows us to define this operation using the previous if/then/else snippet

# Let's start

* Memory: A, 0 
* Cursor: on A
* Input: any

# Process

* set _else_ flag to 1
* while A is not null
  * while A is not null decrease A (aka. reset A)
  * reset _else_ flag
* loop (on an empty cell)
* while _else_ flag is not null
  * increase A
  * reset _else_ flag
* loop (on an empty cell)
* go back to cell A

# Code
```
>+<    set _else_ flag to 1
[      while A is not null
  [-]  while A is not null decrease A (aka reset A)
  >-<  reset _else_ flag
]      loop (on an empty cell)
>[     while _else_ flag is not null
  <+>  increase A
  -    reset _else_ flag
]      loop (on an empty cell)
<      go back to cell A
```

Minified version
```
>+<[[-]>-<]>[<+>-]<
```

# Final state

* Memory: not(A)
* Cursor: on first cell
* Input: unchanged
* Output: unchanged

# Test program

This program does nothing if input is provided, or display 0 if input stream is empty, using not(_input_)

```
,                     read char C
>+<[[-]>-<]>[<+>-]<   get not(C); true if and only if C was empty
[                     while not(C)
  >++++++++           (6)
  [->++++++<]         (x8 = 48)
  >.                  print (48 = '0' ASCII code)
  [-]<<               cleansing
  -                   reset not(C)
]                     loop (on an empty cell)
```
