### Module 3: Comprehending Commands
## Cat: not the pet but the command
cat is most often used for reading out files, like so:

hacker@dojo:~$ cat /challenge/DESCRIPTION.md
One of the most critical Linux commands is `cat`.
*`cat` is most often used for reading out files..*
To obtain the flag
> cat flag 

## Catting absolute paths
cat for an absolute path 

To obtain flag
> cat /flag

## More catting practice 
File is in a hidden directory
cd cmd cannot be used

## grepping for a needle in a haystack 
_grep_: Primarily searches within files for specific patterns or text strings. It operates on the contents of files.

_find_: Searches for files and directories in a filesystem based on various criteria, such as name, type, size, and more. It operates on the file system structure.

to obtain flag
> grep pwn.college

## Listing files
Introduction to *ls* cmd - List files/directories
To obtain the flag
> ls challenge

> /challenge/run

## Touching Files
*touch* cmd introduction - Creation of a file

To Obtain flag
> touch /tmp/pwn
> 
> touch /tmp/college
> 
> /challenge/run

## Removing files
*rm* cmd - Removing files

To obtain flag 
> rm delete_me
> 
> /challenge/check

## Hidden Files
*ls -a* can be used to list hidden files, starting with .`file`

To obtain flag

>cd / #for root directory
>
>ls -a

`cat the hidden file to obtain flag`

## An Epic File System Quest
To obtain the flag use the following clues

>Your first clue is in /. Head on over there.
>Look around with ls. There'll be a file named HINT or CLUE or something along those lines!
>cat that file to read the clue!
>Depending on what the clue says, head on over to the next directory (or don't!). [some directories cant be redirected using cd cmd, so we use ls and cat cmd]

### Making Directories

mkdir command

To obtain the flag
> mkdir /tmp/pwn
>
>ls /tmp


## Linking Files
_*Links come in two flavors: hard and soft (also known as symbolic) links. We'll differentiate the two with an analogy:*_

A hard link is when you address your appartment using multiple addresses that all lead directly to the same place (e.g., Apt 2 vs Unit 2).
A soft link is when you move appartments and have the postal service automatically forward your mail from your old place to your new place.

A symbolic link is a special type of file that serves as a reference to another file or directory. When you access a symlink, it behaves as if you are accessing the original file.

To obtain the flag

