# Module 8: Processes and Jobs

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

  1. /challenge/run
  ```
  I could give you the flag... but I won't, until this process exits.       
     Remember, 
      you can force me to exit with Ctrl-C. Try it now! ^C
    Good job! You have used Ctrl-C to interrupt this process! Here is your flag:pwn.college{4NuYIYsjD8I8YLPmegdxj9HCbEb.dNDN4QDLxIDM2czW} 


---

# Suspending Processes

Suspend processes to the background with Ctrl-Z 

- **To obtain the flag**:

  1. /challenge/run
```
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in 
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         498     213  0 13:48 pts/1    00:00:00 bash /challenge/run
root         500     498  0 13:48 pts/1    00:00:00 ps -f

I don't see a second me!

To pass this level, you need to suspend me and launch me again! You can 
background me with Ctrl-Z or, if you're not ready to do that for whatever 
reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in 
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         498     213  0 13:48 pts/1    00:00:00 bash /challenge/run
root         582     213  0 13:48 pts/1    00:00:00 bash /challenge/run
root         584     582  0 13:48 pts/1    00:00:00 ps -f

Yay, I found another version of me! Here is the flag:
pwn.college{4Wls7-Zl8T_UeyMQpdCStOMserM.dVDN4QDLxIDM2czW}
 ```


---

# Resuming Processes


- **To obtain the flag**:

 1.  /challenge/run
```

 Let's practice resuming processes! Suspend me with Ctrl-Z, then resume me with 
 the 'fg' command! Or just press Enter to quit me! ^Z
 [1]+  Stopped                 /challenge/run
 hacker@processes~resuming-processes:~$ fg /challenge/run
 /challenge/run
 I'm back! Here's your flag:
 pwn.college{Auysc8-oHBMAJhriHm0UARajPL_.dZDN4QDLxIDM2czW}
 Don't forget to press Enter to quit me! 
```


---

# Backgrounding Processes
- **To obtain the flag**:

  1. /challenge/run
  2. ```
     
      To pass this level, you need to suspend me and launch me again! You can 
      background me with Ctrl-Z or, if you're not ready to do that for whatever 
      reason, just hit Enter and I'll exit! 
  3. /challenge/run

---

# Foregrounding Processes
- **To obtain the flag**:

  1. /challenge/run
  2. bg /challenge/run
  3. fg /challenge/run

---

# Starting Backgrounded Processes 
- **To obtain the flag**:

  1. /challenge/run
  2. /challenge/run &
  3. ```
      hacker@processes~starting-backgrounded-processes:~$ Yay, you started me in the background! Because of that, this text will probably 
      overlap weirdly with the shell prompt, but you're used to that by now...  Anyways! Here is your flag! pwn.college{4wubEL68pHbRQizMZbiiBlrIxfi.dlDN4QDLxIDM2czW}
---

# Process Exit Codes
- **To obtain the flag**:
  1. /challenge/submit-code
     ```
       /challenge/submit-code: line 3: /tmp/.code: No such file or directory
        You must run /challenge/submit-code with the exit code you retrieved from 
        /challenge/get-code as the first argument:

  2. /challenge/get-code
  3. echo $?
     ```
     166
  4. /challenge/submit-code 166 


## *_END_* 

