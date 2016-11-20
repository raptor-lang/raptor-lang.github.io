---
title: "RaptorCode"
order: 1
---

The default RaptorScript compiler, [Raptiler](raptiler) compiles to a bytecode called RaptorCode. RaptorCode is then interpreted by [Raptortime](raptortime), the RaptorScript runtime, which is written in rust and stack based.

## How does it work?
RaptorCode is, as mentioned, stack based. This means, it works by pushing operands onto the operand stack, much like reverse polish notation on an old calculator. The advantage of this approach is how easy it is to both compile and interpret, since operand storage is managed pretty much by itself.

Consider the following RaptorScript example:

    var a: Int = 3 + 2

When compiled by the Raptiler, this is the RaptorCode we get:

    CONST 2
    CONST 3
    ADD
    STORE 0

For more information about those instructions, see [instructions](#instructions).

## The Header
The header contains all things meta about this program. In the future, it might hold the name of the module and other related things.

### Magic bytes
A RaptorCode file always starts with these 4 _magic_ bytes:

    5A B7 05 00

  If you look very closely, it might look like the first three bytes spell out _Raptor_. If you can't see it, don't worry, you are neither the first, nor the last.

### Global memory size

!!! warning "Likely to Change"
    
Currently, the amount of fields in global memory, is represented as four bytes, the second item in the header.

## The Constants Table
This is where the magic happens! The constants table will in most cases hold the bulk of your program, unless it is a small procedural script. The reason for this, is that the constants table, among other things, holds all the functions.

### Functions
Functions are the most important content in the constants table, and this is the format they are stored in:

    [id: 4b] [name: terminated by 0x00] [args: 4b] [locals: 4b] [length: 4b] [body: $length bytes]

  1. `id` is the 4 byte unique identifier of this function. Every `CALL` operation will use this identifier.
  2. `name` is the name of the function in RaptorScript. It is a string of characters, terminated by the null byte `0x00`. This name is included mostly for debugging purposes.
  3. `args` is simply the number of arguments this function takes. It is a 4 byte integer.
  4. `locals` is a 4 byte integer telling the interpreter how many local variables this function has.
  5. `length` is a 4 byte integer signifying the length of `body`, in bytes.
  6. `body` is an array of instructions and their arguments. See the [instructions](#instructions) for more info.

## Instructions
Currently, the RaptorCode instruction set is very much in flux, and as such we are currently hosting it [on google sheets](https://docs.google.com/spreadsheets/d/17w3ddipP-RXvodmuAn7Gpf5abjgeEZSU_DFkMI_BZvI/pubhtml?gid=0&single=true), as opposed to here in the docs. This _will_ change in the future, once the language is more stable.
