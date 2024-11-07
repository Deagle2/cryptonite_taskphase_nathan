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

