# If ..., then do ..., else do ...

The second basic instruction in logic flow, after basic if ... then ...

Again, we want to end up at the same memory position whatever the path we choose.

# Let's start

* Memory: A, 0
* Cursor: on A (condition to check)
* Input: any

# Process

* set next cell to 1 (_else_ flag)
* while A is not null
  * do something
  * while A is not null
    * decrease A
  * loop
  * _A=0_
  * reset _else_ flag
* loop (but again A=0)
* go to _else_ flag
* while flag is not null
  * do something else
  * reset _else_ flag
* loop (but flag = 0)
* optionally, go back to A

# Code
```
>+<        set next cell to 1 (else flag)
[          while A is not null
  ...      do something
  [-]      while A is not null decrease A
  >-<      reset else flag
]          loop (on an empty cell)
>          go to else flag
[          while flag is not null
  ...      do something else
  -        reset else flag
]          loop (on an empty cell)
<          optionall, go back to A
```

# Minified version
```
>+<[...[-]>-<]>[...-]<
```

# Final state

* Memory: 0
* Cursor: on 0
* Input: unchanged
* Output: unchanged

# Test program

This code sample displays the char given in input 5 times, or "0" if nothing is provided

```
,              read input
>+<[           if not null
  .....        print value 5 times
[-]>-<]>[      else
  >++++++++    (6)
  [->++++++<]  (x8 = 48)
  >.           print (48 = '0' ASCII code)
  [-]<<        clean and back to original location
-]<
```

