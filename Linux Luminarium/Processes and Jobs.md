# Module 7: Processes and Jobs

## Course Introduction

> Operating system kernels: A kernel is the essential foundation of a computer's operating system (OS). It's the core that provides basic services for all other parts of the OS

>  When Linux starts up, it launches an init (short for initializer) process that, in turn, launches a bunch of other processes which launch more processes until, eventually, you are looking at your command line shell, which is also a process


# Listing Processes
`ps` either stands for "process snapshot" or "process status", and it lists processes. By default, ps just lists the processes running in your terminal
ps aux and ps -ef 
- **To obtain the flag**:
  
>  1. ls /challenge gives permission denied
>  2. ps -ef , a quick run through the processes gives us a process related to the /challenge/run, for me it was /challenge/8584-run-5314
>  3. /challenge/8584-run-5314 to obtain flag
---

# Killing Processes

`kill` will terminate a process in a way that gives it a chance to get its affairs in order before ceasing to exist.

- **To obtain the flag**:

>  1.  ps -ef | grep dont_run
      Output shows : /challenge/dont_run

>  3.  kill /challenge/dont_run
>  4.  kill 72
>  5.  /challenge/run 

---

# Interrupting Processes

The "Ctrl" or "Control" key is so called because it is used to send control characters. Control characters are not actual characters, but are rather used to control the terminal that they are "printed" on. CTRL + C to kill a process

- **To obtain the flag**:

  1.

---

# Suspending Processes

Suspend processes to the background with Ctrl-Z 

- **To obtain the flag**:

  1. 

---

# Resuming Processes


- **To obtain the flag**:

  1. 

---

# Backgrounding Processes
- **To obtain the flag**:

  1.

---

# Foregrounding Processes
- **To obtain the flag**:

  1. 

---

# Starting Backgrounded Processes 
- **To obtain the flag**:

  1. 
---

# Process Exit Codes
- **To obtain the flag**:

  1. 


## *_END_* 

