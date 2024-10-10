# Challenge 6: Practicing Piping

## Course Introduction
Linux has three initial, standard channels of communication. 
- Standard Input (stdin): The default channel where processes receive input.
- Standard Output (stdout): The channel where processes send normal output, such as command results or file contents.
- Standard Error (stderr): The channel used to output error messages when something goes wrong.

## Redirecting Output
- **Description**: 
  The > character is used to redirect the output from a command to a file. In this case, we 
  will redirect the output of the echo command to a file.

- **To obtain the flag**:
  1. In this challenge, you must use this input redirection to write the word PWN (all       
     uppercase) to the filename COLLEGE (all uppercase).
  2. echo PWN > COLLEGE
  
## Redirecting more output

- **To obtain the flag**:
  1. We can give the /challenge/run,  it will give u the following
  2. [INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[FAIL] You did not satisfy all the execution requirements.
[FAIL] Specifically, you must fix the following issue:
[FAIL]   You have not redirected anything for this process' stdout.
5. `running /challenge/run > myflag` only gives the same above output
4.We can do `cat myflag`
3. pwn.college{0wjQVTjo_T7aLMiUbyD6lVgzrul.dVjN1QDLxIDM2czW}
 
## Appending output
- **Description**: 
  A common use-case of output redirection is to save off some command results for later analysis. Often times, you want to do this in aggregate: run a bunch of commands, save their output, and grep through it later. In this case, you might want all that output to keep appending to the same file, but > will create a new output file every time, deleting the old contents.
You can redirect input in append mode using >> instead of >

- **To obtain the flag**:
  1. /challenge/run >> /home/hacker/the-flag
  2. catenate the-flag file
  3. cat the-flag
  4.| 
   \|/ This is the first half:
    v 
pwn.college{MiOXND5YgnhkOLgR5tV0Src007-.ddDM5QDLxIDM2czW}
                              ^
     that is the second half /|\
                              |

If you only see the second half above, you redirected in *truncate* mode (>) 
rather than *append* mode (>>), and so the write of the second half to stdout 
overwrote the initial write of the first half directly to the file. Try append 
mode!
 
     
## Redirecting errors
- **Description**: 
  Just like standard output, you can also redirect the error channel of commands. Here, we'll learn about File Descriptor numbers. A File Descriptor (FD) is a number the describes a communication channel in Linux. You've already been using them, even though you didn't realize it. We're already familiar with three:

FD 0: Standard Input
FD 1: Standard Output
FD 2: Standard Error
*Some FD numbers are implicit. For example, a > without a number implies 1>, which redirects FD 1 (Standard Output).*

- **To obtain the flag**:
  1.  this challenge, you will need to redirect the output of /challenge/run, like before, to myflag, and the "errors" (in our case, the instructions) to instructions
  2. We can start off with /challenge/run 1> myflag 2> instructions
  3. hacker@piping~redirecting-errors:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{sqGCarKpfJT2r8vprx49gL-pJXh.ddjN1QDLxIDM2czW}

## Redirecting Input
- **Description**: 
  [A concise explanation of the concept, command, or wildcard being used.]

- **To obtain the flag**:
  1. [Step-by-step instruction 1]
  2. [Step-by-step instruction 2, if needed]
 
 ## Grepping stored results
- **Description**: 
  [A concise explanation of the concept, command, or wildcard being used.]

- **To obtain the flag**:
  1. [Step-by-step instruction 1]
  2. [Step-by-step instruction 2, if needed]

## Grepping Live Output
- **Description**: 
  [A concise explanation of the concept, command, or wildcard being used.]

- **To obtain the flag**:
  1. [Step-by-step instruction 1]
  2. [Step-by-step instruction 2, if needed]
 

## Grepping errors
- **Description**: 
  [A concise explanation of the concept, command, or wildcard being used.]

- **To obtain the flag**:
  1. [Step-by-step instruction 1]
  2. [Step-by-step instruction 2, if needed]
 
  
## Duplicating piped data with tee
- **Description**: 
  [A concise explanation of the concept, command, or wildcard being used.]

- **To obtain the flag**:
  1. [Step-by-step instruction 1]
  2. [Step-by-step instruction 2, if needed]

## Writing to multiple programs
- **To obtain the flag**:
  1. [Step-by-step instruction 1]
  2. [Step-by-step instruction 2, if needed]


## Splitt-piping stderr and stdout
- **To obtain the flag**:
  1. [Step-by-step instruction 1]
  2. [Step-by-step instruction 2, if needed]
