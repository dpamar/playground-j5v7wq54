# Welcome!

This playground aims to understand the BrainFuck language, sometimes called BF.

The language is really simple to learn, as there are only 8 instructions. It is also a Turing-complete language, so you can virtually implement any algorithm using BF.

However,programs are said to be a bit complex. The goal of this playground is to demonstrate that they aren't !

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
`,       read first char
.       print it
[       while not null
   ,    read next char
   .    print it
]       loop if needed
