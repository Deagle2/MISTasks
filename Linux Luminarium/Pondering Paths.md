
# Module 2: Pondering Paths

## Course Introduction
The Linux filesystem is a "tree". That is, it has a root (written as /). The root of the filesystem is a directory, and every directory can contain other directories and files. You refer to files and directories by their path. A path from the root of the filesystem starts with / (that is, the root of the filesystem), and describes the set of directories that must be descended into to find the file. Every piece of the path is demarcated with another /
  

   ## The Root

- **To obtain the flag**:
  1. /pwn to obtain flag

     ## Program and Absolute Paths
- **To obtain the flag**:
  1. /challenge/run

     ## Position thy self

- **To obtain the flag**:
  1. cd /challenge
  2. ls /challenge
  3. /challenge/run

     ## Position elsewhere
- **Description**: 
  The > character is used to redirect the output from a command to a file. In this case, we 
  will redirect the output of the echo command to a file.

- **To obtain the flag**:
  1./challenge/run
  2. cd /usr/share/build-essential
  3. /challenge/run

     ## Position yet elsewhere

- **To obtain the flag**:
  1. /challenge/run
  2. cd /etc/apt/sources.list.d
  3. /challenge/run

     ## implicit relative paths, from/

- **To obtain the flag**:
  1. /challenge/run
  2. cd /     (root dir.)
  3. challenge/run

     ## explicit relative paths, from/ 


- **To obtain the flag**:
  1. cd /
  2. ./challenge run   (`/challenge/run` will not work)


   ## implicit relative path

- **To obtain the flag**:
  1. cd /
  2. cd challenge
  3. ./run
 
     ## Home sweet Home

  -**To obtain the flag**:
  The constraints are:
Your argument must be an absolute path.
The path must be inside your home directory.
Before expansion, your argument must be three characters or less.
  1. /challenge/run ~/a
