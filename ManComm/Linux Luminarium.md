# [globbing] Multiple Globs

**Flag** - `pwn.college{wwZGdCsewJh9y46egCT10NtkrMZ.QXycTO2EDLxIDM2czW}` 
```
Challenge - We put a few happy, but diversely-named files in /challenge/files. Go cd there and run /challenge/run, providing a single argument: a short (3 characters or less) globbed word with two * globs in it that covers every word that contains the letter p.
```
```
hacker@globbing~multiple-globs:~$ cd /challenge/files
hacker@globbing~multiple-globs:/challenge/files$ /challenge/run
Error: you did not use a wildcard glob...
hacker@globbing~multiple-globs:/challenge/files$ /challenge/files **p
bash: /challenge/files: Is a directory
hacker@globbing~multiple-globs:/challenge/files$ /challenge/run **p
Your expansion did not expand to the requested files (happy optimistic pwning 
splendid uplifting).
Instead, it expanded to:
**p
hacker@globbing~multiple-globs:/challenge/files$ /challenge/run *p*
You got it! Here is your flag!
pwn.college{wwZGdCsewJh9y46egCT10NtkrMZ.QXycTO2EDLxIDM2czW}
```

# [piping] Split-piping stderr and stdout
**Flag** - `pwn.college{kV7aOiZ1D8NdsKHBnBNo7aiZOvx.dFDNwYDLxIDM2czW} `
To redirect stdout to one program and stderr to another. Obtaining the flag was a bit complicated In this challenge, you have:

/challenge/hack: this produces data on stdout and stderr /challenge/the: you must redirect hack's stderr to this program /challenge/planet: you must redirect hack's stdout to this program and combine the knowledge of >(), 2>, and |

To obtain the flag:
I tried various methods and combinations with >(), 2>, and |
In the end I got the flag with the command /challenge/hack 2> >( /challenge/the ) | /challenge/planet
Output: Congratulations, you have learned a redirection technique that even experts struggle with! Here is your flag: `pwn.college{kV7aOiZ1D8NdsKHBnBNo7aiZOvx.dFDNwYDLxIDM2czW} `

# [Silly Shenanigans] Snooping on configurations
`pwn.college{cT0hp1dzbNrjv4pSLV3aryLFtlD.QXyQTM3EDLxIDM2czW}`
