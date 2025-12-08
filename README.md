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


