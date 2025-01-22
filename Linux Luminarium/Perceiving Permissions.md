# Module 9: Perceiving Permissions

# Changing File Ownership
 Intro to chown command, to change the file ownership

 Usage: `chown [username] [file]`

- **To obtain the flag**:

  
  1. ls -l /flag
  2. chown hacker /flag
  3. ls -l /flag
  4. cat /flag
---

# Groups and Files
`id` command
The `chgrp` command in Linux is used to change the group ownership of a file or directory. All files in Linux belong to an owner and a group. 

- **To obtain the flag**:

  1. id
  2. ls -l /flag
  3. chgrp hacker /flag
  4. cat /flag

---

# Fun with Groups Names

- **To obtain the flag**:

  1.id
   ```
   uid=1000(hacker) gid=1000(grp3960) groups=1000(grp3960)
 2. chgrp grp3960 /flag
 3. ls -l /flag
 4. cat /flag

---

# Changing Permissions
Intro to `chmod` (change mode) command

Usage `chmod [OPTIONS] MODE FILE`
eg:-

- **To obtain the flag**:

  1. chmod u+r /flag
  2. cat /flag

---

# Executable Files

- **To obtain the flag**:

  1. chmod +x /challenge/run
  2. /challenge/run

---

# Permission Tweaking Practice

- **To obtain the flag**:
This was a particularly tricky and painstaking task, so I used some help, after 3-4 rounds the challenge becomes simpler 

1.Very big chunk of text, click on the arrow
  <details>
  <summary>Click to expand!</summary>
  
  hacker@permissions~permission-tweaking-practice:~$ /challenge/run
Round 0 (of 8)!

Current permissions of "/challenge/pwn": rw-r--r--
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rwxr--r-x
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions

hacker@permissions~permission-tweaking-practice:~$ chmod u+x,o+x /challenge/pwn
You set the correct permissions!
Round 1 (of 8)!

Current permissions of "/challenge/pwn": rwxr--r-x
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": r--r--r-x
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions

hacker@permissions~permission-tweaking-practice:~$ chmod u-wx /challenge/pwn
You set the correct permissions!
Round 2 (of 8)!

Current permissions of "/challenge/pwn": r--r--r-x
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": ---------
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

hacker@permissions~permission-tweaking-practice:~$ chmod a-rwx /challenge/pwn
You set the correct permissions!
Round 3 (of 8)!

Current permissions of "/challenge/pwn": ---------
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": ------rw-
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions

hacker@permissions~permission-tweaking-practice:~$ chmod o+rw /challenge/pwn
You set the correct permissions!
Round 4 (of 8)!

Current permissions of "/challenge/pwn": ------rw-
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": ---r--rw-
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions

hacker@permissions~permission-tweaking-practice:~$ chmod g+r /challenge/pwn
You set the correct permissions!
Round 5 (of 8)!

Current permissions of "/challenge/pwn": ---r--rw-
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": ------rw-
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions

hacker@permissions~permission-tweaking-practice:~$ chmod g-r /challenge/pwn
You set the correct permissions!
Round 6 (of 8)!

Current permissions of "/challenge/pwn": ------rw-
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rwx---rw-
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions

hacker@permissions~permission-tweaking-practice:~$ chmod u+rwx /challenge/pwn
You set the correct permissions!
Round 7 (of 8)!

Current permissions of "/challenge/pwn": rwx---rw-
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": --x------
- the user doesn't have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

hacker@permissions~permission-tweaking-practice:~$ chmod u-rw,o-rw /challenge/pwn
You set the correct permissions!
You've solved all 8 rounds! I have changed the ownership
of the /flag file so that you can 'chmod' it. You won't be able to read
it until you make it readable with chmod!

Current permissions of "/flag": ---------
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod u+r /flag
hacker@permissions~permission-tweaking-practice:~$ cat /flag
pwn.college{UoF0uaeoJ41Tk0VhojlNiVI5Mb0.dBTM2QDLxIDM2czW}
</details>



---

# Permission Setting Practice

- **To obtain the flag**:

  1. Similar to prev. challenge
    Very big chunk of text, click on the arrow
  <details>
  <summary>Click to expand</summary>

  ```bash
  hacker@permissions~permissions-setting-practice:~$ chmod u-w,o+wx /challenge/pwn
  You set the correct permissions!
  Round 1 (of 8)!

  Current permissions of "/challenge/pwn": r--r--rwx
  * the user does have read permissions
  - the user doesn't have write permissions
  - the user doesn't have execute permissions
  * the group does have read permissions
  - the group doesn't have write permissions
  - the group doesn't have execute permissions
  * the world does have read permissions
  * the world does have write permissions
  * the world does have execute permissions

  Needed permissions of "/challenge/pwn": rw-rwxrwx
  * the user does have read permissions
  * the user does have write permissions
  - the user doesn't have execute permissions
  * the group does have read permissions
  * the group does have write permissions
  * the group does have execute permissions
  * the world does have read permissions
  * the world does have write permissions
  * the world does have execute permissions
  hacker@permissions~permissions-setting-practice:~$ chmod u+w,g+wx /challenge/pwn
  You set the correct permissions!
  Round 2 (of 8)!

  Current permissions of "/challenge/pwn": rw-rwxrwx
  * the user does have read permissions
  * the user does have write permissions
  - the user doesn't have execute permissions
  * the group does have read permissions
  * the group does have write permissions
  * the group does have execute permissions
  * the world does have read permissions
  * the world does have write permissions
  * the world does have execute permissions

  Needed permissions of "/challenge/pwn": r-xr-----
  * the user does have read permissions
  - the user doesn't have write permissions
  * the user does have execute permissions
  * the group does have read permissions
  - the group doesn't have write permissions
  - the group doesn't have execute permissions
  - the world doesn't have read permissions
  - the world doesn't have write permissions
  - the world doesn't have execute permissions
  hacker@permissions~permissions-setting-practice:~$ chmod u=rx,g=r,o=- /challenge/pwn
  You set the correct permissions!
  Round 3 (of 8)!

  Current permissions of "/challenge/pwn": r-xr-----
  * the user does have read permissions
  - the user doesn't have write permissions
  * the user does have execute permissions
  * the group does have read permissions
  - the group doesn't have write permissions
  - the group doesn't have execute permissions
  - the world doesn't have read permissions
  - the world doesn't have write permissions
  - the world doesn't have execute permissions

  Needed permissions of "/challenge/pwn": --x-wxr-x
  - the user doesn't have read permissions
  - the user doesn't have write permissions
  * the user does have execute permissions
  - the group doesn't have read permissions
  * the group does have write permissions
  * the group does have execute permissions
  * the world does have read permissions
  - the world doesn't have write permissions
  * the world does have execute permissions
  hacker@permissions~permissions-setting-practice:~$ chmod u=x,g=wx,o=rx /challenge/pwn
  You set the correct permissions!
  Round 4 (of 8)!

  Current permissions of "/challenge/pwn": --x-wxr-x
  - the user doesn't have read permissions
  - the user doesn't have write permissions
  * the user does have execute permissions
  - the group doesn't have read permissions
  * the group does have write permissions
  * the group does have execute permissions
  * the world does have read permissions
  - the world doesn't have write permissions
  * the world does have execute permissions

  Needed permissions of "/challenge/pwn": r---wxrwx
  * the user does have read permissions
  - the user doesn't have write permissions
  - the user doesn't have execute permissions
  - the group doesn't have read permissions
  * the group does have write permissions
  * the group does have execute permissions
  * the world does have read permissions
  * the world does have write permissions
  * the world does have execute permissions
  hacker@permissions~permissions-setting-practice:~$ chmod u=r,g=wx,o=rwx /challenge/pwn
  You set the correct permissions!
  Round 5 (of 8)!

  Current permissions of "/challenge/pwn": r---wxrwx
  * the user does have read permissions
  - the user doesn't have write permissions
  - the user doesn't have execute permissions
  - the group doesn't have read permissions
  * the group does have write permissions
  * the group does have execute permissions
  * the world does have read permissions
  * the world does have write permissions
  * the world does have execute permissions

  Needed permissions of "/challenge/pwn": r--r--rwx
  * the user does have read permissions
  - the user doesn't have write permissions
  - the user doesn't have execute permissions
  * the group does have read permissions
  - the group doesn't have write permissions
  - the group doesn't have execute permissions
  * the world does have read permissions
  * the world does have write permissions
  * the world does have execute permissions
  hacker@permissions~permissions-setting-practice:~$ chmod u=r,g=r,o=rwx /challenge/pwn
  You set the correct permissions!
  Round 6 (of 8)!

  Current permissions of "/challenge/pwn": r--r--rwx
  * the user does have read permissions
  - the user doesn't have write permissions
  - the user doesn't have execute permissions
  * the group does have read permissions
  - the group doesn't have write permissions
  - the group doesn't have execute permissions
  * the world does have read permissions
  * the world does have write permissions
  * the world does have execute permissions

  Needed permissions of "/challenge/pwn": -w-rw-rwx
  - the user doesn't have read permissions
  * the user does have write permissions
  - the user doesn't have execute permissions
  * the group does have read permissions
  * the group does have write permissions
  - the group doesn't have execute permissions
  * the world does have read permissions
  * the world does have write permissions
  * the world does have execute permissions
  hacker@permissions~permissions-setting-practice:~$ chmod u=w,g=rw,o=rwx /challenge/pwn
  You set the correct permissions!
  Round 7 (of 8)!

  Current permissions of "/challenge/pwn": -w-rw-rwx
  - the user doesn't have read permissions
  * the user does have write permissions
  - the user doesn't have execute permissions
  * the group does have read permissions
  * the group does have write permissions
  - the group doesn't have execute permissions
  * the world does have read permissions
  * the world does have write permissions
  * the world does have execute permissions

  Needed permissions of "/challenge/pwn": rwxrwx---
  * the user does have read permissions
  * the user does have write permissions
  * the user does have execute permissions
  * the group does have read permissions
  * the group does have write permissions
  * the group does have execute permissions
  - the world doesn't have read permissions
  - the world doesn't have write permissions
  - the world doesn't have execute permissions
  hacker@permissions~permissions-setting-practice:~$ chmod u=rwx,g=rwx,o=- /challenge/pwn
  You set the correct permissions!
  You've solved all 8 rounds! I have changed the ownership
  of the /flag file so that you can 'chmod' it. You won't be able to read
  it until you make it readable with chmod!

  Current permissions of "/flag": ---------
  - the user doesn't have read permissions
  - the user doesn't have write permissions
  - the user doesn't have execute permissions
  - the group doesn't have read permissions
  - the group doesn't have write permissions
  - the group doesn't have execute permissions
  - the world doesn't have read permissions
  - the world doesn't have write permissions
  - the world doesn't have execute permissions
  hacker@permissions~permissions-setting-practice:~$ chmod a+rwx /flag
  hacker@permissions~permissions-setting-practice:~$ cat /flag
  pwn.college{8fbNZTZL3J1Bh-tPKu8Oswuf0Es.dNTM5QDLxIDM2czW}


---

# The SUID Bit

"Set User ID" (SUID) permissions bit allows the user to run a program as the owner of that program's file. This means that, regardless of what user runs the program (as long as they have executable permissions), the program will execute as the owner user 
Usage `chmod u+s [program]`

- **To obtain the flag**:

  1.  chmod u+s /challenge/getroot

  2.  /challenge/getroot

> SUCCESS! You have set the suid bit on this program, and it is running as root! Here is your shell...

    3.  cat /flag



## *_END_* 

