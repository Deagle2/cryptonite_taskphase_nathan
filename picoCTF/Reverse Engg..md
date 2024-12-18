# GDB baby step 1

**Flag:** `picoctf{549698}`

---

## How you approached the challenge:

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

## What you learned through solving this challenge:

1. GNU DEBUGGER
2. Assembly Language intro

## References

- [reference 1](https://en.wikipedia.org/wiki/GNU_Debugger)

---

# ARMssembly 1

**Flag:**: `picoCTF{0000001b}`

##  How you approached the challenge:

We're give the following file [chall_1.s](https://mercury.picoctf.net/static/7cc2b73e671f61f8dc2d40493fb62611/chall_1.S)
For what argument does this program print win with variables 81, 0 and 3?

The flag format is picoCTF{XXXXXXXX} -> (hex, lowercase, no 0x, and 32 bits. ex. 5614267 would be picoCTF{0055aabb})

The logic of the given program:

```
str w0, [sp, 12] ;  input x (passed in w0) is stored in [sp + 12]

mov w0, 81          ; w0 = 81
str w0, [sp, 16]    ; 81 stored in [sp + 16]

str wzr, [sp, 20]   ; Stores 0 at [sp + 20]

mov w0, 3           ; w0 = 3
str w0, [sp, 24]    ; stores w0 = 3 at [sp + 24]

ldr w0, [sp, 20]    ; Load 0 into w0
ldr w1, [sp, 16]    ; Load 81 into w1
lsl w0, w1, w0      ; Perform 81 << 0, so w0 = 81
str w0, [sp, 28]    ; Stores 81 at [sp + 28]

ldr w1, [sp, 28]    ; Load 81 into w1
ldr w0, [sp, 24]    ; Load 3 into w0
sdiv w0, w1, w0     ; Perform 81 / 3, so w0 = 27
str w0, [sp, 28]    ; Store 27 at [sp + 28]

```

- So finally [sp + 28] holds the value 27, where result = 27 - x
- If result == 0, the program prints "You win!". This means that the input x also has to be 27

  Finally convert 27 to a zero-padded 8-character hexadecimal string
  1) 27 in decimal = 1B in hexadecimal.
  2) Zero-pad to 8 characters, i.e., add leading zeros until the string is 8 characters long
 
     Giving us the flag as picoCTF{0000001b}


- LDR (Load Register) instructions in ARM architecture are used to load a register with a value from memory
- SDIV is an instruction in ARM that performs signed integer division, taking into account the signs of the two operands


## What you learned through solving this challenge:

1. Basic Assembly Language

  ---

  


