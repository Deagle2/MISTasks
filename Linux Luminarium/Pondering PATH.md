
# Module 12: Pondering Path

## Course Introduction
We have used the following commands earlier

Through an absolute path (e.g., /challenge/run),
through a relative path (e.g., ./run),
through a bare command name (e.g., ls).
The first two cases, the absolute and the relative path case, are straightforward: the run file lives in the /challenge directory. FOr the last case ls: The shell doesn't use a path you provide, but instead looks for the command in the directories listed in your PATH environment variable.

Path is an environment variable that tells the OS where to search for executable files

You can modify path using export ` PATH=$PATH:/your/directory `

# The PATH Variable
You will disrupt the operation of the /challenge/run program. This program will DELETE the flag file using the rm command. However, if it can't find the rm command, the flag will not be deleted, and the challenge will give it to you! Thus, you must make it so that /challenge/run also can't find the rm command

- **To obtain the flag**:
  1. PATH=""
     We set PATH = nothing by giving an empty string, this deletes the rm command and we can run the challenge
  2. /challenge/run
---

# Setting PATH
/challenge/run will run the win command via its bare name, but this command exists in the /challenge/more_commands/ directory, which is not initially in the PATH. The win command is the only thing that /challenge/run needs, so you can just overwrite PATH with that one directory.
- **To obtain the flag**:
  1. /challenge/run
> Invoking 'win'.... /challenge/run: line 4: win: command not found
It looks like that did not work... Did you set PATH correctly?
  2. PATH=/challenge/more_commands/
  3. /challenge/run
> Invoking 'win'....

>   Congratulations! You properly set the flag and 'win' has launched!
  pwn.college{kjeis7e5_yRZiFznu08xTZlFfLR.dVzNyUDLxIDM2czW}


---

# Adding Commands
- **To obtain the flag**:
  1. Make a file with the command cat /flag
    name as win.sh in the directory /home/hacker
  2. Run `chmod +x win.sh` to make file executable
  3. `export PATH=/home/hacker:$PATH`
  4. `mv win.sh w`
  5. `/challenge/run`
  ```
  Invoking 'win'....
  pwn.college{kYI9KZuaf7cx26Zgw3JLUPR1fMN.dZzNyUDLxIDM2czW}
  
  
- Kept getting an error/didnt get the flag at first when running /challenge/run, due to not renaming win.sh to win
- The mv command in Linux is used to move or rename files and directories. 
---

# Hijacking Commands
- **To obtain the flag**:
  1. Make a file called `rm` with the command `cat /flag` as before even without the challenge explicitly stating, I saved rm in /home/hacker
  2. chmod +x rm
  3. export PATH=/home/hacker:$PATH
  4. rm gives cat: /flag: Permission denied
  5. /challenge/run
  > Trying to remove /flag...
    Found 'rm' command at /home/hacker/rm. Executing!
    pwn.college{sEkbwTZtmCjnPnG6fLmiUNMKfD6.ddzNyUDLxIDM2czW}

---


## *_END_* 
