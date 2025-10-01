# [globbing] Multiple Globs
`pwn.college{wwZGdCsewJh9y46egCT10NtkrMZ.QXycTO2EDLxIDM2czW}` 
# [piping] Split-piping stderr and stdout
To redirect stdout to one program and stderr to another. Obtaining the flag was a bit complicated In this challenge, you have:

/challenge/hack: this produces data on stdout and stderr /challenge/the: you must redirect hack's stderr to this program /challenge/planet: you must redirect hack's stdout to this program and combine the knowledge of >(), 2>, and |

To obtain the flag:
I tried various methods and combinations with >(), 2>, and |
In the end I got the flag with the command /challenge/hack 2> >( /challenge/the ) | /challenge/planet
Output: Congratulations, you have learned a redirection technique that even experts struggle with! Here is your flag: `pwn.college{kV7aOiZ1D8NdsKHBnBNo7aiZOvx.dFDNwYDLxIDM2czW} `

# [Silly Shenanigans] Snooping on configurations
`pwn.college{cT0hp1dzbNrjv4pSLV3aryLFtlD.QXyQTM3EDLxIDM2czW}`
