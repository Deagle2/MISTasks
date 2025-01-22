#  Module 6: Practicing Piping

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
3. `running /challenge/run > myflag` only gives the same above output

4.We can do `cat myflag`

5. pwn.college{0wjQVTjo_T7aLMiUbyD6lVgzrul.dVjN1QDLxIDM2czW}
 
## Appending output
- **Description**: 
  A common use-case of output redirection is to save off some command results for later analysis. Often times, you want to do this in aggregate: run a bunch of commands, save their output, and grep through it later. In this case, you might want all that output to keep appending to the same file, but > will create a new output file every time, deleting the old contents.
You can redirect input in append mode using >> instead of >

- **To obtain the flag**:
  ```
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
mode!```
 
     
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
  3. `hacker@piping~redirecting-errors:~$` cat myflag

[FLAG] Here is your flag:

[FLAG] pwn.college{sqGCarKpfJT2r8vprx49gL-pJXh.ddjN1QDLxIDM2czW}

## Redirecting Input
- **Description**: 
  You can redirect input to programs using `<`
 
`hacker@dojo:~$ cat message`

yo

`hacker@dojo:~$ rev < message`

oy

- **To obtain the flag**:
  1. In this level, we will practice using /challenge/run, which will require you to redirect the PWN file to it and have the PWN file contain the value COLLEGE! To write that value to the PWN file, recall the prior challenge on output redirection from echo!

  2. We use `echo COLLEGE > PWN` to write COLLEGE to the PWN file

  3.  /challenge/run < PWN    
Reading from standard input...
Correct! You have redirected the PWN file into my standard input, and I read 
the value 'COLLEGE' out of it!
Here is your flag:
pwn.college{cEVeLi4CjsSI-lG30M_wsqc46bN.dBzN1QDLxIDM2czW}

`PWN file has the same value of COLLEGE`
 
 ## Grepping stored results
- **Description**:
- Usage of `>` and `grep` command
- Rhe next part of Practicing Piping introduces us to the pipe operator a mix of > and grep
  

- **To obtain the flag**:
- ```
  Redirect the output of /challenge/run to /tmp/data.txt.
This will result in a hundred thousand lines of text, with one of them being the flag, in /tmp/data.txt.
Grep that for the flag!

  1. Redirect the output `/challenge/run >  /tmp/data.txt`
  2. finding any string that matches with pwn.college in /tmp/data.txt
  3. `hacker@piping~grepping-stored-results:~$` grep pwn.college /tmp/data.txt
      pwn.college{woG7sVmwCRfyYleK1zpxbmXQfE3.dhTM4QDLxIDM2czW}

## Grepping Live Output
- **Description**: 
  Introduction to | (pipe) operator

  Standard output from the command to the left of the pipe will be connected to (piped into) the standard input of the command to the right of the pipe

- **To obtain the flag**:
- `/challenge/run` will output a hundred thousand lines of text, including the flag. Grep for the flag!
  1. challenge/run give a big output, 
we can see the following in the output
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt
  2. `/challenge/.data.txt` but bash: /challenge/.data.txt: Permission denied as output
  3. So since I know pwn.college is in the flag I used the pipe operator to find the flag in the output of /challenge/run
  4. /challenge/run | grep pwn.college
  5. pwn.college{kaL8h5rE_2IpnJvaM8N0xjaWBrF.dlTM4QDLxIDM2czW}
 

## Grepping errors
- **Description**: 
  The shell has a >& operator, which redirects a file descriptor to another file descriptor.
  We redirect standard error to standard output (2>& 1) and then pipe the now-combined stderr   and stdout as normal (|)

- **To obtain the flag**:
  1. `/challenge/run 2>& 1 | grep pwn.college `
   
 
  
## Duplicating piped data with tee
- **Description**: 
  This process' /challenge/pwn must be piped into /challenge/college, but you'll need to       
  intercept the data to see what pwn needs from you!

- **To obtain the flag**:
  1. challenge/pwn | /challenge/college
  ` We get an the output as `Processing...
The input to 'college' does not contain the correct secret code! This code 
should be provided by the 'pwn' command. HINT: use 'tee' to intercept the 
output of 'pwn' and figure out what the code needs to be.`
2. /challenge/pwn | tee output.txt | /challenge/college
3. cat output.txt
4. We get `hacker@piping~duplicating-piped-data-with-tee:~$ cat output.txt`
Usage: /challenge/pwn --secret [SECRET_ARG]

SECRET_ARG should be "su3IUXZp"`
5. /challenge/pwn --secret su3IUXZp | /challenge/college


## Writing to multiple programs
Process Substitution method

 In this challenge, we have /challenge/hack, /challenge/the, and /challenge/planet. Run the /challenge/hack command, and duplicate its output as input to both the /challenge/the and the /challenge/planet commands
 
- **To obtain the flag**:
  1.  In this challenge, we have /challenge/hack, /challenge/the, and /challenge/planet. Run the /challenge/hack command, and duplicate its output as input to both the /challenge/the and the /challenge/planet commands!
  2. `/challenge/hack | tee >(/challenge/the) | /challenge/planet`
Congratulations, you have duplicated data into the input of two programs! Here 
is your flag:
pwn.college{QucI4WoDHekh81yn2urwzmYrj29.dBDO0UDLxIDM2czW}


`>(/challenge/the)` is the process substitution. Sending the duplicated output from tee to `/challenge/the`.



## Splitt-piping stderr and stdout
To redirect stdout to one program and stderr to another.
Obtaining the flag was a bit complicated
In this challenge, you have:

/challenge/hack: this produces data on stdout and stderr
/challenge/the: you must redirect hack's stderr to this program
/challenge/planet: you must redirect hack's stdout to this program
and combine the knowledge of >(), 2>, and |
- **To obtain the flag**:
  1. I tried various methods and combinations with >(), 2>, and |
  2. In the end I got the flag with the command ` /challenge/hack 2> >( /challenge/the ) | /challenge/planet `
  3. Output: Congratulations, you have learned a redirection technique that even experts 
struggle with! Here is your flag:
pwn.college{kV7aOiZ1D8NdsKHBnBNo7aiZOvx.dFDNwYDLxIDM2czW}
`


### *_END_*
