# Module 10: Untangling Users
## Course Introduction
`sudo` , `su`  and `John the ripper` tool introduction
`su`: Substitutes the user, switches the current user to another user account.
`sudo`(Superuser Do) :sudo is a program for Unix-like computer operating systems that enables users to run programs with the security privileges of another user, by default the superuser.


# Becoming Root with su

- **To obtain the flag**:
  1. Enter su cmd
  2. Give the password : hack-the-planet
  3. cat /flag
---

# Other users with su

- **To obtain the flag**:
  1. su zardus
  2. zardus' pwd is dont-hack-me
  3. /challenge/run

---

# Cracking Passwords

- **To obtain the flag**:
  1. cd /challenge
  2. cat shadow-leak
  3. john shadow-leak
     ```
     Loaded 1 password hash (crypt, generic crypt(3) [?/64])
      Press 'q' or Ctrl-C to abort, almost any other key for status
      aardvark         (zardus)
      1g 0:00:00:21 100% 2/3 0.04728g/s 275.3p/s 275.3c/s 275.3C/s Johnson..buzz
      Use the "--show" option to display all of the cracked passwords reliably
     Session completed
  4. john --show shadow-leak
     ```
     We get zardus:aardvark:20011:0:99999:7:::
     
  5. su zardus and give password as `aardvark`
  6. /challenge/run

---

# Using sudo

- **To obtain the flag**:
  1. sudo cat /etc/shadow
  2. sudo cat /flag

---

## *_END_* 
