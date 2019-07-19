# If ..., then do ...

The very basic instruction in logic flow. The goal here is to execute a piece of code if and only if a value is true (i.e. not null).

And ideally, regardless of the boolean value, we want to end up at the same memory position. This is not mandatory, but it's really useful to know where we are in the memory, whatever might have been done earlier.

# Let's start

* Memory: A
* Cursor: on A (condition to check)
* Input: any

# Process

* while A is not null
  * do something
  * while A is not null
    * decrease A
  * loop
  * _A=0_
* loop (but, wait, A=0, so the _something_ is executed only once)

# Code
```
[     while A is not null
  ... do something
  [-] while A is not null decrease A
]     loop (i.e. stop)
```

# Minified version
```
[...[-]]
```

# Final state

* Memory: 0
* Cursor: on 0
* Input: unchanged
* Output: unchanged
