
use bash. zsh and fish are just user friendliness added on top. (like extra ones we dont need, in a way everything is user friendliness)


every shell has three standard streams
- stdin - send data into a program or command. entering a command into the shell or the input from another program into another one is also stdin.
- stdout
- stderr

what goes in, what comes out, and the errors. 

if we dont have access to the stdin, then its called as non-interactive.

0 - stdin, 1 - stdout, 2 - stderr
2>&1 -> redirect stderr to stdout

cat file.txt >> output.txt (append)


append `&` to make it run in the background

&& -> make sure that rhs is executed only if lhs ran successfully
|| -> make sure that right side command is executed only if the left side command fails

echo $? - get the exit code of last run command


use export MY_VAR = 'kevin', to create and set an env
`unset` to remove

`alias <alias name>='<command>'`

```
alias ciaclean='git branch --merged origin/main | grep -vE "^\s*(\*|main|develop)" | xargs -n 1 git branch -d'
```

---

#!/bin/bash - bash interpreter
#!/usr/bin/python - python interpreter

in the start of the script, tells us what interpreter will execute this.
