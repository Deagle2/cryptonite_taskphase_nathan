# Buffer Overflow 0

**Flag:** `picoCTF{ov3rfl0ws_ar3nt_that_bad_ef01832d}`

## How you approached the challenge:

- We are given 2 files, on opening vuln.c we can inspect the code. We see that the program has used strcpy and gets functions which are not safe, meaning they do not have "boundary checks", which means we can do buffer overflow.
- char buf2[16] in line 17 means 16 bytes is allocated to buf2 (buffer size of 16), meaning the program might overflow if the input exceed 16 bytes.
- Hint 2 : If you try to do the math by hand, maybe try and add a few more characters. Sometimes there are things you aren't expecting.
- After connecting using netcat `nc  saturn.picoctf.net 52504` we have to input the a number of characters, in order to get the flag we try to do buffer overflow
- Using the hint we can try adding a few more characters, by trial and error method I found out that 19 characters is the breaking point/buffer overflow point.
- This meant that at 20 characters input I got the flag as seen in the screenshot below
  ![image](https://github.com/user-attachments/assets/defeced7-8fd8-4422-89f8-f596da5fbec1)
Cmd 1 has 19 characters
Cmd 2 has 20 characters which was the breaking point/buffer overflow


- Logic behind this was a bit confusing so after asking chatgpt the reason. I figured out that when the input is 19 characters, the first 16 fill buf2, and the 17th, 18th, and 19th characters overwrite part of the saved frame pointer. Although buf2 is at 16 bytes, there might be padding (extra space for performance reason) added by the compiler between buf2 and the saved frame pointer.
- " Saved Frame pointer: a register used by high-level language compilers to track the current stack frame "


## What you learned through solving this challenge:

1. I learnt that strcpy and gets are dangerous functions as they do not check the size of the buffers, which can lead to binary exploitation: Buffer Overflow
example in gets:
```
char buffer[10];
gets(buffer) 
```
Here if your string is more than 9 characters it will lead to buffer overflow
2. On doing ` man gets ` under the BUGS section:
```
 Never use gets().Because it is impossible to tell without knowing the data in advance how many characters gets() will read,
 and because gets() will continue to store characters past the end of the buffer, it is extremely dangerous to use.  
It has been used to break computer security.  Use fgets() instead.
```
3. strncpy and fgets are the better safer alternatives
   For example fgets allows you to specify max number of characters to read, which prevents overflow
`fgets(buffer, sizeof(buffer), stdin);`
Here the input of the user may be "infinite" but the program will only read the specified amount of characters/bytes


## References

- [man gets BUGS section](http://cwe.mitre.org/data/definitions/242.html)
- [https://stackoverflow.com/questions/76786373/as-programmers-do-we-have-to-care-about-struct-padding-in-the-context-of-pointer](https://stackoverflow.com/questions/76786373/as-programmers-do-we-have-to-care-about-struct-padding-in-the-context-of-pointer)
---

# format string 0

**Flag:** `picoCTF{7h3_cu570m3r_15_n3v3r_SEGFAULT_dc0f36c4}`

## How you approached the challenge:

- Upon launching the instance, you were given a command to connect with the challenge instance

```
nc mimas.picoctf.net 61301
```

- nc (Netcat) is a networking tool used in linux
- We are given 2 hints: This is an introduction of format string vulnerabilities. "Look up "format specifiers" if you have never seen them before." 
& "Just try out the different options". We can try out the second hint to obtain the flag in 2 steps 


```
Welcome to our newly-opened burger place Pico 'n Patty! Can you help the picky customers find their favorite burger?
Here comes the first customer Patrick who wants a giant bite.
Please choose from the following burgers: Breakf@st_Burger, Gr%114d_Cheese, Bac0n_D3luxe
```

- For the above you had to enter the name of correct "burger", which we can guess as `Gr%114d_Cheese`

```
Gr                                                                                                           4202954_Cheese
Good job! Patrick is happy! Now can you serve the second customer?
Sponge Bob wants something outrageous that would break the shop (better be served quick before the shop owner kicks you out!)
Please choose from the following burgers: Pe%to_Portobello, $outhwest_Burger, Cla%sic_Che%s%steak
```

- Out of Breakf@st_Burger, Gr%114d_Cheese and Bac0n_D3luxe, `Gr%114d_Cheese` is the only string containing a format specifier `%`. In this context it is known as a width specifier (`%114`)

- Out of Pe%to_Portobello, $outhwest_Burger and Cla%sic_Che%s%steak, `Cla%sic_Che%s%steak` worked as it contains `%s`, a format specifier 
 


![blob](https://github.com/user-attachments/assets/5670d55a-db8f-4254-ac90-14bfb4074de9)



## What you learned through solving this challenge:

1. Format Specifiers - Format specifiers in C are used to define the type of data to be printed or scanned in input and output operations. They always start with a % symbol and are used in functions like printf(), scanf(), sprintf(). It is used together with the printf() function to tell the compiler what type of data the variable is storing. It is basically a placeholder for the variable value.

%d - For signed integer type.

%s -string

Eg:- %2d - means min. width of 2 characters for an integer output



2. Format string Vulnerabilities - Attackers can exploit format specifiers like printf with user input



## Other incorrect methods you tried:

- Looking for the flag inside the shared files

References

- [Format Specifiers](https://www.geeksforgeeks.org/format-specifiers-in-c/)
- [C Variables Format Spec.](https://www.w3schools.com/c/c_variables_format.php)

---

# flag leak

**Flag:** `picoCTF{L34k1ng_Fl4g_0ff_St4ck_999e2824}`

How you approached the challenge:

- We are given 2 files vuln.c and the program file, we're also given the hint `format strings` which points to a format string vulnerability ( %p, %s, %x etc) just like the `format string 0` challenge
- I tried giving the input as `%x` and `%p` which gave me random memory addresses and `%s` which did not give me any output.
-  The main vulnerability lies here
```
scanf("%127s", story); 
   printf(story)
``` 
-scanf reads up to 127 chars from the input and printf treats the input of the story variable as a format string, i.e., %x, %s, %p are read by printf and not counted as a string/text

- Since this was a complex challenge I took help from various resources of the internet eg:- John Hammond
- We can do a trial-and-error approach with `%n$s` or `gdb` debug the program
   Although trial and error is not practical, I managed to find the flag with `%24$s`
- Here in the `printf` function, the 24th position in the stack contains the address to the flag variable and when the `%s` specifier is used it takes the value at that location, treats it as a memory address and then tries to read the string that is located at that memory address, which in this case, is the flag.

What you learned through solving this challenge:

1. Format String exploits ( by exploiting printf)


References

- [reference 1](https://youtu.be/DhVRI33s-D0?si=eiJbsuf477Veeer-)
