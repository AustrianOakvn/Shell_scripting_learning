# Shell scripting tutorial

## A first script

File: my-script.sh \
Run: ./my-script.sh \
The first line tells Unix that the file is going to be executed by /bin/sh \
Commend line is marked with "#" 

## Variables

File: var.sh \
File: var2.sh \
Declaration VAR=value \
There is no space between. VAR = value doesn't work \
The shell does not care about the type of variables, they may store strings, integers, real number or anything. They are all stored as strings. \
You can interactively set variable names using read command
Run: 
```shell
$ MYVAR=hello
$ ./myvar2.sh
MYVAR is:
MYVAR is: hi there
```
When **myvar2.sh** is called, a new shell is spawned to run the script, for MYVAR to be understood by another program, we need **export**. \

```shell
$ export MYVAR
$ ./myvar2.sh
MYVAR is: hello
MYVAR is: hi there
```
When **myvar2.sh** exits, MYVAR keeps its value of hello. If we want it to receive new change from the script, we must source the script. We source a script via "." (dot) command.
```shell
$ MYVAR=hello
$ echo MYVAR
hello
$ . ./myvar2.sh
MYVAR is: hello
MYVAR is: hi there
$ echo $MYVAR
```

Change has now been made it out into our shell. This is how **.profile** or **.bash_profile** file works

```shell
#!/bin/sh
echo "What is your name?"
read USER_NAME
echo "Hello $USER_NAME"
echo "I will create you a file called $USER_NAME_file"
touch $USER_NAME_file
```
This will lead to error because there is no variable USER_NAME_file

Fix by user.sh
```shell
#!/bin/sh
echo "What is your name?"
read USER_NAME
echo "Hello $USER_NAME"
echo "I will create you a file called ${USER_NAME}_file"
touch "${USER_NAME}_file"
```
The quotes around ensure that if user enter "Steve Parker", the the argument pass to touch would be Steve and Parker file, which produce 2 separated files.


## Acknowledgement
I followed the tutorial from: [Link](https://www.shellscript.sh/)
