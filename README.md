# Shell-Scripting-for-DevOps-Engineers

## Self Assessment

**_1.What does this line in shell scripts means?: `#!/bin/bash`_**

- `#!/bin/bash` is She-bang

- `/bin/bash` is the most common shell used as default shell for user login of the linux system. The shell’s name is an acronym for Bourne-again shell. Bash can execute the vast majority of scripts and thus is widely used because it has more features, is well developed and better syntax.

**_2.True or False? When a certain command/line fails in a shell script, the shell script, by default, will exit and stop running_**

- Depends on the language and settings used. If the script is a bash script then this statement is true. When a script written in Bash fails to run a certain command it will keep running and will execute all other commands mentioned after the command which failed.

- Most of the time we might actually want the opposite to happen. In order to make Bash exist when a specific command fails, use 'set -e' in your script.

**_3.What do you tend to include in every script you write?_**

- Few example:
  - Comments on how to run it and/or what it does
  - If a shell script, adding "set -e" since I want the script to exit if a certain command failed
  - 
- You can have an entirely different answer. It's based only on your experience and preferences.

**_4.Today we have tools and technologies like Ansible, Puppet, Chef, ... Why would someone still use shell scripting?_**

- Speed
- Flexibility
- The module we need doesn't exist (perhaps a weak point because most CM technologies allow to use what is known as "shell" module)
- We are delivering the scripts to customers who don't have access to the public network and don't necessarily have Ansible installed on their systems.

## Variables

**_5.How to define a variable with the value "Hello World"?_**

- `HW="Hello World`

**_6.How to define a variable with the value of the current date?_**

- `DATE=$(date)`

**_7.How to print the first argument passed to a script?_**

- `echo $1`

**_8.Write a script to print "yay" unless an argument was passed and then print that argument._**

- `echo "${1:-yay}"`

**_9.What would be the output of the following script?_**

-**_ `#!/usr/bin/env bash` _**
-**_ `NINJA_TURTLE=Donatello` _**
-**_ `function the_best_ninja_turtle {` _**
-**_         `local NINJA_TURTLE=Michelangelo` _**
-**_         `echo $NINJA_TURTLE` _**
-**_ `}` _**
-**_ `NINJA_TURTLE=Raphael` _**
-**_ `the_best_ninja_turtle` _**

- Michelangelo

**_10.Explain what would be the result of each command:_**
- **_echo $_** -> Prints the name of the shell or the shell script being executed.
- **_echo $?_** -> Prints the exit status (return code) of the most recently executed foreground command.
- **_echo $$_** -> Prints the Process ID (PID) of the current shell instance.
- **_echo $#_** -> Prints the number of positional parameters passed to the shell or shell script.

**_11.What is $@?_**

- `$@` is a special shell variable that expands to the full list of all positional parameters passed to a script, function, or shell, starting from `$1`, `$2`, and so on.
- When used unquoted (`$@`), the shell treats it as separate arguments (`$1` `$2` `$3`...).

- When used double-quoted (`"$@"`), the shell treats it as separate, individually quoted strings (`"$1"` `"$2"` `"$3"`...), which is the preferred and safest way to preserve arguments containing spaces or special characters.

12.What is difference between $@ and $*?

- `$@` is an array of all the arguments passed to the script
- `$*` is a single string of all the arguments passed to the script

**_13.How do you get input from the user in shell scripts?_**

- Using the keyword `read` so for example `read x` will wait for user input and will store it in the variable x.

**_14.How to compare variables length?_**

- `if [ ${#1} -ne ${#2} ]; then`
    `...`
