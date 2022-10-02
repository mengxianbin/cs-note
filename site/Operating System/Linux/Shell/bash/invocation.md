[Home](https://mengxianbin.github.io) /
[cs-notes](https://mengxianbin.github.io/cs-notes/site) /
[Operating System](https://mengxianbin.github.io/cs-notes/site/Operating%20System) /
[Linux](https://mengxianbin.github.io/cs-notes/site/Operating%20System/Linux) /
[Shell](https://mengxianbin.github.io/cs-notes/site/Operating%20System/Linux/Shell) /
[bash](https://mengxianbin.github.io/cs-notes/site/Operating%20System/Linux/Shell/bash) /
[invocation](https://mengxianbin.github.io/cs-notes/site/Operating%20System/Linux/Shell/bash/invocation)

```man
INVOCATION
       A login shell is one whose first character of argument zero is a -, or one started with the --login option.

       An interactive shell is one started without non-option arguments (unless -s is specified) and without the -c option whose standard input and error are both connected to terminals (as determined by isatty(3)), or one started with the -i option.  PS1       
       is set and $- includes i if bash is interactive, allowing a shell script or a startup file to test this state.

       The following paragraphs describe how bash executes its startup files.  If any of the files exist but cannot be read, bash reports an error.  Tildes are expanded in filenames as described below under Tilde Expansion in the EXPANSION section.

       When bash is invoked as an interactive login shell, or as a non-interactive shell with the --login option, it first reads and executes commands from the file /etc/profile, if that file exists.  After reading that file, it looks for ~/.bash_profile,       
       ~/.bash_login, and ~/.profile, in that order, and reads and executes commands from the first one that exists and is readable.  The --noprofile option may be used when the shell is started to inhibit this behavior.

       When an interactive login shell exits, or a non-interactive login shell executes the exit builtin command, bash reads and executes commands from the file ~/.bash_logout, if it exists.

       When an interactive shell that is not a login shell is started, bash reads and executes commands from /etc/bash.bashrc and ~/.bashrc, if these files exist.  This may be inhibited by using the --norc option.  The --rcfile file option will force bash       
       to read and execute commands from file instead of /etc/bash.bashrc and ~/.bashrc.

       When  bash  is started non-interactively, to run a shell script, for example, it looks for the variable BASH_ENV in the environment, expands its value if it appears there, and uses the expanded value as the name of a file to read and execute.  Bash       
       behaves as if the following command were executed:
              if [ -n "$BASH_ENV" ]; then . "$BASH_ENV"; fi
       but the value of the PATH variable is not used to search for the filename.

       If bash is invoked with the name sh, it tries to mimic the startup behavior of historical versions of sh as closely as possible, while conforming to the POSIX standard as well.  When invoked as an interactive login shell, or a non-interactive shell       
       with  the  --login  option,  it  first attempts to read and execute commands from /etc/profile and ~/.profile, in that order.  The --noprofile option may be used to inhibit this behavior.  When invoked as an interactive shell with the name sh, bash       
       looks for the variable ENV, expands its value if it is defined, and uses the expanded value as the name of a file to read and execute.  Since a shell invoked as sh does not attempt to read and execute commands from  any  other  startup  files,  the       
       --rcfile option has no effect.  A non-interactive shell invoked with the name sh does not attempt to read any other startup files.  When invoked as sh, bash enters posix mode after the startup files are read.

       When  bash  is started in posix mode, as with the --posix command line option, it follows the POSIX standard for startup files.  In this mode, interactive shells expand the ENV variable and commands are read and executed from the file whose name is       
       the expanded value.  No other startup files are read.

       Bash attempts to determine when it is being run with its standard input connected to a network connection, as when executed by the remote shell daemon, usually rshd, or the secure shell daemon sshd.  If bash determines it is being run in this fash‐       
       ion,  it  reads  and executes commands from ~/.bashrc and ~/.bashrc, if these files exist and are readable.  It will not do this if invoked as sh.  The --norc option may be used to inhibit this behavior, and the --rcfile option may be used to force       
       another file to be read, but neither rshd nor sshd generally invoke the shell with those options or allow them to be specified.

       If the shell is started with the effective user (group) id not equal to the real user (group) id, and the -p option is not supplied, no startup files are read, shell functions are not inherited from the environment, the SHELLOPTS, BASHOPTS, CDPATH,       
       and GLOBIGNORE variables, if they appear in the environment, are ignored, and the effective user id is set to the real user id.  If the -p option is supplied at invocation, the startup behavior is the same, but the effective user id is not reset.
```
