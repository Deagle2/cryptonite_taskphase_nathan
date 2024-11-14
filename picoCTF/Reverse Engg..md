# GDB baby step 1

**Flag:** `picoctf{549698}`

How you approached the challenge:

- We have to find out the value in the eax register at the end of the main function and we're given a file `debugger0_a`
- We are given 2 hints, gdb debugger and use of main
- On installing gdb and running
```gdb debugger0_a
```
-  Run `(gdb) info functions` to  identify the address of the main function, which we see at 00....001129 

```
(gdb) disassemble main
``` 
The above command disassembles the main fucntion which givwfwe

What you learned through solving this challenge:

1. GNU DEBUGGER


References

- [reference 1](https://en.wikipedia.org/wiki/GNU_Debugger)
