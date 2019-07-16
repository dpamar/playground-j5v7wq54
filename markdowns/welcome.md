# Welcome!

This playground aims to understand the BrainFuck language, sometimes called BF.

The language is really simple to learn, as there are only 8 instructions. It is also a Turing-complete language, so you can virtually implement any algorithm using BF.

However,programs are said to be a bit complex. The goal of this playground is to demonstrate that they aren't !

In case you're wondering : the cover image is the source code of a BF interpreter, written in BF ^^. This will be part of a future playground :-)

# Let's start

BF is executed on a memory array. By default, it's a 30k-cell-long array of 8-bit integers, but some other implementations are more flexible.

There are two registers : Instruction pointer and Memory Pointer.

Finally, there are 8 instructions:
* `>` : Move memory pointer to the right and go to next instruction
* `<` : Move memory pointer to the left and go to next instruction
* `+` : Increment memory cell and go to next instruction
* `-` : Increment memory cell and go to next instruction
* `,` : Read char from input and store in memory then go to next instruction
* `.` : Write memory value as ASCII char to output then go to next instruction
* `[` : Go to next instruction if cell is not null, or to the matching closing "]" if null
* `]` : Go back to the matching opening "[" if cell is not null, or go to next instruction if null

# Simple program : cat

In BF, the easiest code sample is not hello world, it's a BF implementation of Unix `cat` command.

cat copies input chars to output. In BF, we just have to

```
1 ,       read first char
2 .       print it
3 [       while not null (go to 7 if null)
4    ,    read next char
5    .    print it
6 ]       loop if needed (go back to 3) or go to 7
7 nothing
```

Note : any char other than the 8 instructions is considered as a comment. It's really easier to read this source code than the same one-line version
```
,.[,.]
```

