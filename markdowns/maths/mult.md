# Multiply numbers

Multiplication (AxB) is a math algorithm to avoid doing B successive additions.
However, BF does not even allows additions : as explained we can only increase or decrease values !

If additions are implemented using "successive +1", then multiplications will be done using "successive successive +1"

To compute AxB, we'll have to sum B, A times. And, as sum destroys operands, we need to copy B for the next loop.

# Let's start

* Memory: A, B, 0, 0
* Cursor: on A
* Input: any

# Process

4 cells : [m,n,o,p]
* while m is not null
  * _invariant : p=Bx(A-m) + (B-n), o= B-n_
  * while n is not null
    * decrease n
    * increase o
    * increase p
  * loop
  * while o is not null
    * decrease o
    * increase n
  * loop
  * decrease m
* loop
* _m=0, n=B, p=BxA, o=0_
* and optionally, do some cleansing

# Code

```
[       while m is not null
  >[    while n is not null
    -   decrease n
    >+  increase o
    >+  increase p
  <<]   loop
  >[    while o is not null
    -   decrease o
    <+  increase n
  >]    loop
  <<-   decrease m
]       loop

```

# Minified version

```
[>[->+>+<<]>[-<+>]<<-]
```

# Final state

* Memory: 0, B, 0 , AxB
* Cursor: on first cell
* Input: unchanged
* Output: unchanged

# Optional cleansing

* Move result to first cell
* Clear second cell

```
[>[->+>+<<]>[-<+>]<<-]  mult
>[-]                    clear second cell
>>[-<<<+>>>]<<<         move result
```

# Test program

```
++++++++++               (10)
>+++++<                  (5)
[>[->+>+<<]>[-<+>]<<-]   multiply
>[-]>>[-<<<+>>>]<<<      cleansing
.                        print 5x10 = 50 ('2' in ASCII)
```
