# Module 4: Digesting Documentation
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


## Searching for Manuals
Introduction to `man man` command

## To obtain the flag
>man man
>
>man -k challenge
>
> man zmsndlmaid

CHALLENGE(1)                                      Challenge Commands                                      CHALLENGE(1)

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

       --zmsndl NUM
              print the flag if NUM is 191

AUTHOR
       Written by Zardus.

REPORTING BUGS
       The repository for this dojo: <https://github.com/pwncollege/linux-luminarium/>

SEE ALSO
       man(1) bash-builtins(7)

pwn.college                                            May 2024                                           CHALLENGE(1)

> /challenge/challenge --zmsndl 191
> 
> pwn.college{MXzGX1mWRsA91QPHndERlPm61ai.dZTM4QDLxIDM2czW}

## Helpful Programs
To obtain the flag
run the command 
> /challenge/challenge -h

This will give you all arguments, -p prints the secret code needed for flag, -g gets the flag
> /challenge/challenge -g `-code (I couldn't save)`
> Flag is printed

## Help for Builtins
This challenge is relatively simple

To obtain the flag
``` 
hacker@man~help-for-builtins:~$ help challenge
challenge: challenge [--fortune] [--version] [--secret SECRET]
    This builtin command will read you the flag, given the right arguments!
    
    Options:
      --fortune         display a fortune
      --version         display the version
      --secret VALUE    prints the flag, if VALUE is correct

    You must be sure to provide the right value to --secret. That value
    is "49MIWj-p".
hacker@man~help-for-builtins:~$ challenge --secret 49MIWj-p
Correct! Here is your flag!
pwn.college{49MIWj-pajUI0KOnYeWuyQ1DxIF.dRTM5QDLxIDM2czW}```


