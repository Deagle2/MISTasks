# Module 5: File Globbing

## Course Introduction
Globbing lets you reference files without typing them all out, or typing out their full paths. File globbing allows you to use wildcards to create flexible patterns for searching files.

## Matching with `*`
- **Description**: When it encounters a `*` character in any argument, the shell will treat it as "wildcard" and try to replace that argument with any files that match the pattern.

- **To obtain the flag**:
  > You can make an argument of any type with less than 4 characters
  > 
  > Here I have done cd /ch*
  > 
  > /challenge/run to get flag
  
### Matching with `?`
- **Description**: The `?` wildcard matches a single character in a file name. Similar to `*`  wildcard 

- **To obtain the flag**:
  > use the cd command with the ? wildcard to substitute for the letters c and l
  > 
  > cd /?ha??enge
  > 
  > /challenge/run to get verify and get flag

Use Case:
The ? wildcard is often used when:

You know the structure of the name but aren't sure about certain characters.
You want to match multiple files or directories where only a few characters differ.

###  Matching with `[]`
- **Description**: Square brackets allow you to specify a set of characters to match.
- 
The square brackes are, essentially, a limited form of ?, in that instead of matching any character, [] is a wildcard for some subset of potential characters, specified within the brackets. For example, [pwn] will match the character p, w, or n.

- **To obtain the flag**:
  > cd /challenge/files
  > 
  > Match the constraints given :- a,b,h,s files
  > 
  > /challenge/run file_[abhs]


### Matching paths with `[]`
- **Description**: Use brackets to match directories or paths.
  
- **To obtain the flag**:
  >run /challenge/run with a single argument that bracket-globs into the absolute paths to the    file_b, file_a, file_s, and file_h files!
  >
  > /challenge/run /challenge/files/file_[bash]
  >
  > the bracket characters can be of any order

### Mixing Globs
- **Description**: Combine different wildcards for complex searches.
   
- **To obtain the flag**:
  > Firstly we have to change directory
  > 
  > cd /challenge/files
  > 
  > There isnt much common with the 3 unique words so we use
  > 
  > ls ??a*  , `*`the shell will treat it as "wildcard" and try to replace that argument with any files that match the pattern.
  > 
  > amazing  beautiful  challenging are 3 words we get but not a flag
  > 
  > /challenge/run [cep]* is the only way to get the required flag
  > 
  > [cep]: This is a character set, meaning it will match any file or directory that starts with c, e, or p.

### Exclusionary Globbing
- **Description**: Exclude certain patterns using the `!` operator.

- **To obtain the flag**:
  > change directory
  > 
  > cd /challenge/files
  > 
  > Obviously /challenge/run [abcdefghijklmoqrstuvxyz] will not work, returning the error of argument not having more than 8 characters
  > 
  > /challenge/run [!pwn] doesnt work, it returns the following error
  >
  > Your expansion did not expand to the requested files (amazing beautiful 
challenging delightful educational fantastic great happy incredible jovial kind 
laughing magical optimistic queenly radiant splendid thrilling uplifting 
victorious xenial youthful zesty).
Instead, it expanded to:
[!pwn]^
  > 
  > /challenge/run [!pwn]* gets the required flag
  > 
  > pwn.college{AuULO6V92VoFf3zpwYreeh4me3Q.dZjM4QDLxIDM2czW}

 Without the *, the pattern would only match files with a single character that is not "p," "w," or "n." In other words, without *, it would only match files that are exactly one character long.

_END_
