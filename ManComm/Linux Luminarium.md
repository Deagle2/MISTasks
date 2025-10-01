# [globbing] Multiple Globs

**Flag** - `pwn.college{wwZGdCsewJh9y46egCT10NtkrMZ.QXycTO2EDLxIDM2czW}` 
```
Challenge - We put a few happy, but diversely-named files in /challenge/files. Go cd there and run /challenge/run, providing a single argument: a short (3 characters or less) globbed word with two * globs in it that covers every word that contains the letter p.
```
```Idris
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
```yaml
Challenge : In this challenge, you have:

/challenge/hack: this produces data on stdout and stderr
/challenge/the: you must redirect hack's stderr to this program
/challenge/planet: you must redirect hack's stdout to this program
```
You must redirect hack's stdout to this program and combine the knowledge of >(), 2>, and |
I tried various methods and combinations with >(), 2>, and |
In the end I got the flag with the command `/challenge/hack 2> >( /challenge/the ) | /challenge/planet`
```
Output: Congratulations, you have learned a redirection technique that even experts struggle with! Here is your flag: `pwn.college{kV7aOiZ1D8NdsKHBnBNo7aiZOvx.dFDNwYDLxIDM2czW} `
```

# [Silly Shenanigans] Snooping on configurations
**Flag** -`pwn.college{cT0hp1dzbNrjv4pSLV3aryLFtlD.QXyQTM3EDLxIDM2czW}`

Neet trick I found was instead of `cat /home/zardus/.bashrc` we could use the grep command: ` grep -E '^FLAG_GETTER_API_KEY=' /home/zardus/.bashrc`
```javascript
hacker@practice~shenanigans~snooping-on-configurations:~$ ls -l /home
total 4
drwxr-xr-x 1 hacker hacker  638 Oct  1 16:16 hacker
drwxr-xr-x 2 zardus zardus 4096 Oct  1 16:16 zardus
hacker@practice~shenanigans~snooping-on-configurations:/home/zardus$ cat /home/zardus/.bashrc
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
case $- in
    *i*) ;;
      *) return;;
esac

# don't put duplicate lines or lines starting with space in the history.
# See bash(1) for more options
HISTCONTROL=ignoreboth

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=1000
HISTFILESIZE=2000

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# If set, the pattern "**" used in a pathname expansion context will
# match all files and zero or more directories and subdirectories.
#shopt -s globstar

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "${debian_chroot:-}" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
    xterm-color|*-256color) color_prompt=yes;;
esac

# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
#force_color_prompt=yes

if [ -n "$force_color_prompt" ]; then
    if [ -x /usr/bin/tput ] && tput setaf 1 >&/dev/null; then
        # We have color support; assume it's compliant with Ecma-48
        # (ISO/IEC-6429). (Lack of such support is extremely rare, and such
        # a case would tend to support setf rather than setaf.)
        color_prompt=yes
    else
        color_prompt=
    fi
fi

if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
*)
    ;;
esac

# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'
fi

# colored GCC warnings and errors
#export GCC_COLORS='error=01;31:warning=01;35:note=01;36:caret=01;32:locus=01:quote=01'

# some more ls aliases
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'

# Add an "alert" alias for long running commands.  Use like so:
#   sleep 10; alert
alias alert='notify-send --urgency=low -i "$([ $? = 0 ] && echo terminal || echo error)" "$(history|tail -n1|sed -e '\''s/^\s*[0-9]\+\s*//;s/[;&|]\s*alert$//'\'')"'

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if ! shopt -oq posix; then
  if [ -f /usr/share/bash-completion/bash_completion ]; then
    . /usr/share/bash-completion/bash_completion
  elif [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
  fi
fi
FLAG_GETTER_API_KEY=sk-1159516847
hacker@practice~shenanigans~snooping-on-configurations:/home/zardus$ flag_getter --key sk-1159516847
Correct API key! Do you want me to print the flag (y/n)?
y
pwn.college{practice}


```
