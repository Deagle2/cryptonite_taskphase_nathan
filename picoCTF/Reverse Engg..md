# GDB baby step 1

**Flag:** `picoctf{549698}`

---

# How you approached the challenge:

- We have to find out the value in the eax register at the end of the main function and we're given a file `debugger0_a`
- We are given 2 hints, gdb debugger and use of main
- On installing gdb and running
```
gdb debugger0_a
```
-  Run `(gdb) info functions` to  identify the address of the main function, which we see at 00....001129 

```
(gdb) disassemble main
``` 
- The above command disassembles the main function which gives us an output, where I saw the value 0x86342 next to eax, meaning eax holds the value 0x86342. 

- The given value is in hexadecimal representation, on converting we get 549698, therefore we obtain the flag by adding `picoctf{}`. 

---

# What you learned through solving this challenge:

1. GNU DEBUGGER
2. Assembly Language intro

# References

- [reference 1](https://en.wikipedia.org/wiki/GNU_Debugger)

  ---

  


