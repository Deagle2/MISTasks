# Module 7: Shell Variables

## Course Introduction
Command line interface `(CLI)` is colloquially referred to as a "shell", programs written in this language are referred to as "shell scripts". 
When you're using the command line, you are basically writing a shell script line by line

#  Printing Variables

`You print out variables with echo, by prepending the variable name with a $`

- **To obtain the flag**:

  1.echo $FLAG
 
---

# Setting Variables

You can write values to variables. This is done, as with many other languages, using =. To set variable VAR to value 1337, you would use:

hacker@dojo:~$ VAR=1337
(there are no spaces around the =)

- **To obtain the flag**:
  
  1. PWN=COLLEGE
         
    You've set the PWN variable properly! As promised, here is the flag:
    pwn.college{kyyhUY7Dy2YucvvKoUghv1_5myN.dlTN1QDLxIDM2czW}

---

# Multi-word variables

Quoting/using " like in python as a string, for a word that has spaces

- **To obtain the flag**:
  
  1. PWN="COLLEGE YEAH"

You've set the PWN variable properly! As promised, here is the flag:
pwn.college{Ua46XZVZM6i6JS-U3xYfnU8gSvg.dBjN1QDLxIDM2czW}

---

# Exporting Variables


- **To obtain the flag**:
  
  1. PWN=COLLEGE
  2. export PWN
  3. COLLEGE=PWN
  4. `export -n COLLEGE` to make sure that COLLEGE is not exported
  5. `hacker@variables~exporting-variables:~$ /challenge/run`

    CORRECT!
  
    You have exported PWN=COLLEGE and set, but not exported, COLLEGE=PWN. Great job! Here is your flag:pwn.college{s7ZnUsABgMwhc520PKiC4XmObXm.dJjN1QDLxIDM2czW}
  
    You've set the PWN variable to the proper value!
  
    You've set the COLLEGE variable to the proper value!
    

---

#  Printing Exported Variables

`env` command introduction wil print out every exported variable set in your shell

- **To obtain the flag**:
  
  1. Simply typing `env` gave me a lot of random text
  2. We can use a previously learnt operator to find the flag
  3. `env | grep pwn.college`
  4. env | grep pwn.college
  ```
     VSCODE_PROXY_URI=https://pwn.college/workspace/code/proxy/{{port}}/
      FLAG=pwn.college{QvmureKMpoXkR3F9EQBb0dCFCqX.dhTN1QDLxIDM2czW}
     
---

# Storing Command Output

Command substitution allows you to assign the output of a shell command to a variable. This one of the most useful feature of shell scripts. After assigning the output to a variable, you can use the stored value anywhere in your shell scripts. This is useful when processing data in your scripts

- **To obtain the flag**:


  1. PWN=$(/challenge/run)

     Congratulations! You have read the flag into the PWN variable. Now print it out and submit it!
  2. echo "$PWN"
      ```
      pwn.college{kSdV-213KmXzYRd9DdKw6VPOm4P.dVzN0UDLxIDM2czW}

---

# Reading Input

> `read` reads data from the standard input, `-p` is an argument to display a prompt message to the user before reading the input.

- **To obtain the flag**:

  1. read -p "INPUT: " PWN
      INPUT: COLLEGE

      ```
      You've set the PWN variable properly! As promised, here is the flag:
      pwn.college{IQ-gHSqCbfl4evCaWIhLPJ8_MIX.dhzN1QDLxIDM2czW}

---

# Reading Files

`read pwn` reads input and assigns it to the PWN variable
`< /challenge/read_me:` redirects /challenge/read_me fileb info into the standard input of the read command, i.e. PWN variable in this case

- **To obtain the flag**:
  
  1. read PWN < /challenge/read_me
     
     ```  
      You've set the PWN variable properly! As promised, here is the flag:
      pwn.college{s0F8JVtlMxoRFyKpKrHZica48jz.dBjM4QDLxIDM2czW}

---


## *_END_* 
