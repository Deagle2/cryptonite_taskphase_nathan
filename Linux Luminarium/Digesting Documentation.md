# Challenge 4: Digesting Documentation

## Learning from Documentation

To obtain the flag:

> The program for this challenge is `/challenge/challenge`. You will need to pass it the argument of `--giveflag`.
>
> Run the command:
>
> ```bash
> /challenge/challenge --giveflag
> ```

## Learning Complex Usage

To obtain the flag:

> The `/challenge/challenge` program allows you to print arbitrary files to the terminal when given the `--printfile` argument. 
> 
> We can assume that the flag of the challenge will be somewhere under `/flag` or similar.
>
> So we use:
>
> ```bash
> /challenge/challenge --printfile /flag
> ```

## Reading Manuals

The `man` (manual) command is essentially a helper/guide for each command. When you're done reading the man page, you can hit `q` to quit.

> The challenge in this level has a secret option that, when used, will cause the challenge to print the flag. You must learn this option through the man page for `challenge`!
>
> We can try:
>
> ```bash
> man challenge
> ```

Running `man challenge` gives us the following man page:






