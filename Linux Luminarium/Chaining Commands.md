# Module 11: Chaining Commands

## Course Introduction

Introduction to chaining cmd. Chaining is different from Piping


Chaining lets you run multiple commands that are independent of each other 
- 
Usage `/challenge/pwn  ; /challenge/college `
There are other types of chaining commands such as 

`&&` - Runs the next command only if the previous command succeeds 

and

 `||`- Runs the next command only if the previous command fails

Piping takes the output of 1st command and passes it as input to the 2nd command as learnt in previous modules
-
- Usage `ls -l | grep ".txt"`

# Chaining with semicolons
To chain /challenge/pwn and /challenge/college

- **To obtain the flag**:
  1. /challenge/pwn  ; /challenge/college
---

# Your First Shell Script
Run /challenge/pwn and then /challenge/college, but this time in a shell script called x.sh

- **To obtain the flag**:
  1. Make a new text file x.sh, my directory was /home/hacker/x.sh
  2. /challenge/pwn and /challenge/college cmds in file
  3. `bash x.sh` in terminal

---

# Redirecting Script Output
In this level, we will practice piping (|) from your script to another program. Like before, you need to create a script that calls the /challenge/pwn command followed by the /challenge/college command, and pipe the output of the script into a single invocation of the /challenge/solve command

- **To obtain the flag**:
  1. Make a new text file, I made my_script.sh, put the commands /challenge/pwn and /challenge/college
  2. ` chmod +x my_script.sh `, to make your script executable.
  3. Pipe the output ` ./my_script.sh | /challenge/solve `
     
---

# Executable Shell Scripts
Make a shellscript that will invoke /challenge/solve, make it executable, and run it without explicitly invoking bash

- **To obtain the flag**:
  1. As the challenge wasn't that clear, using external help we understand the use of #!/bin/bash
  2. The #!/bin/bash at the top tells the system to use bash to interpret the script.
  3. Make a new text file x.sh and type
      #!/bin/bash
      /challenge/solve
  4. In the terminal, `chmod +x x.sh` 
  5. `./x.sh `

---

## *_END_* 
