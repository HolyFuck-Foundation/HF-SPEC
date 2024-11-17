# HF-SPEC
Official HolyFuck(tm) specification.

## Operators
| Command | Description |
|---------|-------------|
| + | Increment value at the memory pointer [wrapping] |
| - | Decrement value at the memory pointer [wrapping] |
| > | Move memory pointer 1 byte to the right [wrapping] |
| < | Move memory pointer 1 byte to the left [wrapping] |
| [ | Jump past the matching ] if the byte at the memory pointer is 0 |
| ] | Jump back to the matching [ if the byte at the memory pointer is nonzero |
| . | Push the byte at the memory pointer to the stack |
| , | Pop a byte from the stack and write it to the current memory pointer |
| $ | Starts an assembly instruction |
| ; | Ends an assembly instruction or function call |
| : | Defines a function (see (Functions)[#functions]) |
| @ | Calls a function |

## Functions
Functions are defined as follows:
```bf
:showme{
    +++[-]
}
```
Functions can be called as such:
```bf
:main{
    @showme
}
```
Because the stack is shared throughout the entire program, there is no need for function arguments. Just make sure to pop the right values to the stack, and the function can read these and act upon them. Isn't that simple?

Functions can also have ANY characters in the name, except `{` (in function declarations) and `;` (in function calls)!
Example:
```bf
:sorry
    for_👍++this{
  +++[-]
}

:main{
  @sorry
    for_👍++this;
}
```

## Example
```
:test{
  $real asm instruction
}

:main{
  @test
}
```
