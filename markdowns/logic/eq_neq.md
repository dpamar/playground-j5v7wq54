# Evaluate Eq() and Neq() functions

To check if 2 values A and B are equal, we need to compute A-B. Either the result is 0 (then A == B) or not (then A != B)

In other words, "A-B" = Neq(B) because result is true if and only if A<>B

The Eq() function is a bit more tricky, it combines Neq and Not functions.

# Let's start

* Memory: A, B 
* Cursor: on A
* Input: any

# Process for Neq

* while B is not null
  * _invariant : d=A-B is constant_
  * decrease B
  * decrease A
* loop
* _B=0, so A=d_
* go back to cell A

# Process for Eq

* set else flag after B
* compute A-B as explained above
* while A is not null
  * reset A and else flag
* loop (on null value)
* while else flag is not null
  * set A to 1
  * reset else flag
* loop (on null value)
* go back to cell A

# Code for Neq
```
>[    while B is not null
  -   decrease B
  <-> decrease A
]     loop
<     go back to cell A
```

Minified version
```
>[-<->]<
```

# Code for Eq
```
>>+        set else flag
<[         while B is not null
  -        decrease B
  <->      decrease A
]          loop
<[         while A is not null
  [-]>>-<< reset A and else flag
]          loop (on null value)
>>[        while else flag is not null
  <<+      set A to 1
  >>-      reset else flag
]          loop (on null value)
<<         go back to cell A
```

Minified version
```
>>+<[-<->]<[[-]>>-<<]>>[<<+>>-]<<
```

# Final state

* Memory: Neq(A) or Eq(A)
* Cursor: on first cell
* Input: unchanged
* Output: unchanged

# Test program

These programs read 2 chars, and print both if different, or just a unique one if equal.

```
,>,            read A and B
[-<->>+<]      double trick : computes A minus B on the left and copy B on the right
<[             A != B
  >>[-<+<+>>]  reconstruct A and B original values from B copy
  <<.[-]       print A and clean
  >.[-]        print B and clean
<]             loop (on null value)
>>[            go to B copy (if not deleted then it means A == B)
  .[-]         print B (aka A and print only once) and clean
]<<            cleansing
```

Details: memory is
* When A == B:
  * A B 0 then subtract/copy B
  * 0 0 B as A == B
  * _nothing done from first cell_
  * _B printed from third cell, then cleansing_
  * Final state 0 0 0
* When A != B: d=A-B
  * A B 0 then subtract/copy B
  * d 0 B with d not null
  * _from first cell, B added back to d and 0_
  * A B 0
  * _A printed and clean from first cell_
  * _B printed and clean from second cell_
  * _nothing done from third cell_
  * Final state 0 0 0
Hence, only unique values are displayed, with a final state 0 0 0 in both cases
