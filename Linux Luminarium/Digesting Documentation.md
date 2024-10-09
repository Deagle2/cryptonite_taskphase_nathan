# Challenge 4: Digesting Documentation
## Learning from Documentation

To obtain the Flag
> The program for this challenge is /challenge/challenge
> you will need to pass it the argument of --giveflag
>
> Run the cmd /challenge/challenge --giveflag

## Learning Complex Usage

To obtain the flag

> /challenge/challenge program allows you to print arbitrary files to the terminal, when given the --printfile argument
> We can assume that the flag of the challenge will be somewhere under /flag or similar
> So we use /challenge/challenge --printfile /flag

## Reading Manuals

Introduction to man (manual) cmd, a command basically like a helper/guide for each command 
When you're done reading the manpage, you can hit q to quit.

> The challenge in this level has a secret option that, when you use it, will cause the challenge to print the flag. You must learn this option through the man page for challenge!
> We can try
> man challenge
> man challenge gives manpage:

CHALLENGE(1)                       Challenge Commands                       CHALLENGE(1)

NAME
       /challenge/challenge - print the flag!

SYNOPSIS
       challenge OPTION

DESCRIPTION
       Output the flag when called with the right arguments.

       --fortune
              read a fortune

       --version
              output version information and exit

       --gpgjru NUM
              print the flag if NUM is 447

AUTHOR
       Written by Zardus.

*From here we can can try challenge --gpgjru 447*
but challenge: command not found
so we can try 
> ./challenge --gpgjru 447
> 
> flag is obtained!

## Searching Manuals

continuation of earlier challenge

To obtain the Flag

> man challenge
>
> there are 1800+ arguments, so I had to do forward search and type _/flag_, scrolled until I found  **--yje  This argument will give you the flag!**
> /challenge/challenge --yje to obtain the flag
