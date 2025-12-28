# Shell-Scripting-for-DevOps-Engineers

![Bash Script](https://img.shields.io/badge/bash_script-%23121011.svg?style=for-the-badge&logo=gnu-bash&logoColor=white)

![](ShellScripting.png)

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

## Conditionals

**_15.Explain conditionals and demonstrate how to use them._**

- Conditionals allow the shell to execute different code blocks based on whether a test expression (evaluated using `if` with `[ ]` or `(( ))`) is true or false.

- `# Checks if file exists`
- `if [ -f /etc/hosts ]; then`
-   `echo "Hosts file found."`
- `fi`

- `# Checks if 10 is greater than 5`
- `NUM=10`
- `if (( NUM > 5 )); then`
-   `echo "True."`
- `else`
-   `echo "False."`
- `fi`

**_16.In shell scripting, how to negate a conditional?_**

- In shell scripting (Bash), you negate a conditional test using the `!` (exclamation mark) operator.

**_17.In shell scripting, how to check if a given argument is a number?_**

- `regex='^[0-9]+$'`
- `if [[ ${var//*.} =~ $regex ]]; then`
- `...`

## Arithmetic Operations

**_18.How to perform arithmetic operations on numbers?_**

- One way: `$(( 1 + 2 ))`
- Another way: `expr 1 + 2`

**_19.How to perform arithmetic operations on numbers?_**

- The easiest way to perform arithmetic operations on integers is using the double parenthesis syntax, `(( ... ))`.

- You can perform standard operations like addition (`+`), subtraction (`-`), multiplication (`*`), and division (`/`) directly inside. To save the result to a variable, you wrap the expression with a dollar sign: `RESULT=$(( 5 * 10 - 2 ))`. Variables inside the parentheses (e.g., `A` in `A + 1`) do not need the dollar sign prefix. For operations involving floating-point numbers (decimals), you must use the external command `bc`.

**_20.How to check if a given number has 4 as a factor?_**

- `if [ $(($1 % 4)) -eq 0 ]; then`

## Loops

**_21.What is a loop? What types of loops are you familiar with?_**

- A loop is a fundamental programming construct that allows a block of code (the loop body) to be executed repeatedly based on a control condition. This repetition continues until the condition is no longer met, preventing redundant coding.

- 3 Types of Loops:
  - 1.`for loop`: Iterates over a list of items, executing once for each item in a list or range (e.g., Processing every file in a directory).

  - 2.`while loop`: Repeats a block of code as long as a specified conditional test remains true (e.g., Waiting for a log file to contain a specific entry).

  - 3.`until loop`: Repeats a block of code as long as a specified conditional test remains false (e.g., Retrying a network connection until it succeeds).
 
**_22.Demonstrate how to use loops._**

- Three main loop types:
  - 1.`for` Loop (Iterating over a list): This loop runs once for each item listed in the `do...done` block.

    - `for FILE in file1.txt file2.txt file3.txt; do`
    -   `echo "Processing $FILE"`
    -   `done`

  - 2.`while` Loop (Condition is true): This loop continues executing as long as the condition (`[ $COUNT -lt 3 ]`) remains true.
 
    - `COUNT=0`
    - `while [ $COUNT -lt 3 ]; do`
    -   `echo "Count is $COUNT"`
    -   `COUNT=$((COUNT + 1))`
    - `done`
 
  - 3.`until` Loop (Condition is false): This loop continues executing until the condition (`[ -f /tmp/data.lock ]`) becomes true (i.e., until the file exists).
 
    - `until [ -f /tmp/data.lock ]; do`
    - `echo "Waiting for lock file..."`
    - `done`

## Troubleshooting

**_23.How do you debug shell scripts?_**

- Answer depends on the language you are using for writing your scripts. If Bash is used for example then:
  - Adding -x to the script I'm running in Bash
  - Old good way of adding echo statements

- If Python, then using pdb is very useful.

**_24.Running the following bash script, we don't get 2 as a result, why?_**
- **_x = 2_**
- **_echo $x_**

- Should be `x=2`

## Substring

**_25.How to extract everything after the last dot in a string?_**

- `${var//*.}`

**_26.How to extract everything before the last dot in a string?_**

- `${var%.*}`

## Misc

**_27.Generate 8 digit random number._**

- `shuf -i 9999999-99999999 -n 1`

**_28.Can you give an example to some Bash best practices?_**

- Four essential Bash scripting best practices:
  - 1.Use Shebang: Always start scripts with `#!/bin/bash` (or `#!/usr/bin/env bash`) to ensure the correct interpreter is used.

  - 2.Error Handling (Crucial!): Include `set -euo pipefail` at the top. This ensures the script exits immediately on errors (`-e`), handles unset variables (`-u`), and checks pipeline failures (`-o pipefail`).

  - 3.Quote Variables: Always use double quotes (`"..."`) around variable expansions (e.g., `"$VAR"`) to prevent word splitting and globbing issues.

  - 4.Use Functions: Break complex scripts into smaller, reusable functions.

**_29.What is the ternary operator? How do you use it in bash?_**

- A short way of using if/else. An example:

- `[[ $a = 1 ]] && b="yes, equal" || b="nope"`

**_30.What does the following code do and when would you use it?_**
- **_diff <(ls /tmp) <(ls /var/tmp)_**

- It is called 'process substitution'. It provides a way to pass the output of a command to another command when using a pipe | is not possible. It can be used when a command does not support STDIN or you need the output of multiple commands.

**_31.What are you using for testing shell scripts?_**

- bats

