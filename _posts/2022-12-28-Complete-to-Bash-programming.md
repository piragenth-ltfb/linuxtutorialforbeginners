---
author: piragenth
title: "Bash Guide For Beginners | complete guide to the Bash"
date: 2022-12-28T14:56:35+05:30
draft: false
categories:
- Linux
- bash
tags:
- bash
- linux
---

![](https://linuxtutorialforbeginners.com/assets/Pictures/bash-script.png)

Welcome to this comprehensive tutorial on bash scripting! Bash scripting is a powerful tool for automating tasks and making them more efficient. It is widely used in the Linux and Unix world, and it can be a useful skill for any system administrator or developer.

In this tutorial, we will cover everything you need to know to get started with bash scripting. We will start by introducing the basics of bash scripting, including the syntax and common commands. We will then move on to more advanced topics such as loops, functions, and variables. By the end of this tutorial, you will have a solid foundation in bash scripting and be able to write your own scripts to automate tasks and improve your workflow.

Before we dive into the tutorial, let's first define what bash scripting is and how it works.

# What is bash scripting?

Bash scripting is a way of writing scripts or programs using the Bash shell, which is the default shell on many Linux and Unix systems. The Bash shell is a command-line interface (CLI) that allows users to interact with the operating system by typing commands and executing scripts.

Bash scripts are written in a text file and saved with a .sh extension. They can be executed from the command line by typing "bash script.sh" or by making the script executable and running it with "./script.sh".

Bash scripts can perform a wide range of tasks, from simple tasks such as displaying a message on the screen to complex tasks such as automated backups or server deployments.

# Why learn bash scripting?


There are several reasons why you might want to learn bash scripting:

* It is a widely used and powerful tool. Bash is the default shell on many Linux and Unix systems, and it is used by system administrators and developers around the world. Knowing how to write bash scripts will make you a more valuable and versatile employee or freelancer.
* It can save you time and effort. Bash scripts allow you to automate tasks and reduce the amount of manual work you have to do. This can save you a lot of time and effort, especially if you have to perform the same tasks repeatedly.
* It is easy to learn. Bash scripting is relatively easy to learn, especially if you already have some programming experience. The syntax is simple and straightforward, and there are plenty of resources available to help you learn.

# Getting started with bash scripting
Before you can start writing bash scripts, you need to have a Bash shell installed on your system. If you are using a Linux or Unix system, chances are you already have Bash installed. If you are using a Windows system, you can install Bash by downloading and installing the Windows Subsystem for Linux (WSL).

Once you have Bash installed, you can start writing bash scripts by creating a text file and saving it with a .sh extension. You can use any text editor to create the script, such as vi, emacs, or even a simple text editor like Notepad.

To execute a bash script, you can either run it from the command line by typing "bash script.sh" or make it executable by using the chmod command and then running it with "./script.sh".

Here is a simple example of a bash script that displays a message on the screen:

``` bash 
#!/bin/bash
echo "Hello, World!"
```

To run this script, save it as hello.sh and then execute it with the following command:

```bash
bash hello.sh
```
You should see the message "Hello, World!" displayed on the screen.

# Bash 
## Bash script syntax
Now that you know how to create and run a bash script, let's take a look at the syntax and some common commands used in bash scripting.

## Comments
In bash scripts, you can add comments by using the "#" symbol. Comments are used to explain what the script does or to add notes for yourself or others. Anything after the "#" symbol on a line is treated as a comment and is ignored by the script.

For example: 

```bash
# This is a comment
echo "Hello, World!" # This is also a comment
```
## Variables
In bash scripts, you can use variables to store and manipulate data. Variables are denoted by a dollar sign ($), and they can contain numbers, strings, or arrays.

To assign a value to a variable, use the following syntax:

```bash
var_name=value
```
For example:

```bash
name="john"
age=30
```

To use a variable in a script, use the dollar sign and the variable name, like this:

```bash
echo "My name is $name and I am $age years old."
```
Bash script syntax
Now that you know how to create and run a bash script, let's take a look at the syntax and some common commands used in bash scripting.

Comments
In bash scripts, you can add comments by using the "#" symbol. Comments are used to explain what the script does or to add notes for yourself or others. Anything after the "#" symbol on a line is treated as a comment and is ignored by the script.

For example:

```bash
# This is a comment
echo "Hello, World!" # This is also a comment
```
Variables
In bash scripts, you can use variables to store and manipulate data. Variables are denoted by a dollar sign ($), and they can contain numbers, strings, or arrays.

To assign a value to a variable, use the following syntax:

```bash
var_name=value
```
For example:

```bash
name="John"
age=30
```
To use a variable in a script, use the dollar sign and the variable name, like this:

```bash
echo "My name is $name and I am $age years old."
```
This will output "My name is John and I am 30 years old."

You can also use variables in arithmetic operations by enclosing them in double parentheses, like this:

```bash
((result = 5 + 3))
echo "The result is $result."
```
This will output 'The result is 8."

## Commands

In bash scripts, you can use commands to perform actions or manipulate data. There are many built-in commands available in Bash, such as echo, which we used in the previous examples to display messages on the screen.

To use a command in a bash script, simply type the command followed by any arguments or options. For example:

```bash
echo "Hello, World!" # Displays a message on the screen
ls -l # Lists the contents of the current directory in long format
```

You can also use external commands or programs in your bash scripts by specifying the full path to the executable file. For example:

```bash
/usr/bin/python my_script.py # Executes a Python script
```

# Conditionals
Conditionals allow you to execute different commands or blocks of code based on a certain condition. In bash scripts, you can use the if statement to execute a block of code if a condition is true.

The syntax for an if statement is as follows:


```bash 
if [ condition ]; then
  # code to execute if condition is true
else
  # code to execute if condition is false
fi
```

For example:

```bash
age=20

if [ $age -gt 18 ]; then
  echo "You are an adult."
else
  echo "You are a minor."
fi
```

This will output "You are an adult."

You can also use the elif statement to specify additional conditions to check. For example:

```bash
age=17
if [ $age -gt 18 ]; then
  echo "You are an adult."
elif [ $age -gt 12 ]; then
  echo "You are a teenager."
else
  echo "You are a child."
fi
```

## Loops

Loops allow you to execute a block of code multiple times. In bash scripts, you can use the for and while loops to execute a block of code based on a certain condition.

The syntax for a for loop is as follows:

```bash
for var in list; do
  # code to execute for each element in list
done
```

For example:

```bash
for i in 1 2 3 4 5; do
  echo "Iteration $i"
done
```

This will output "Iteration 1", "Iteration 2", "Iteration 3", "Iteration 4", and "Iteration 5".

The syntax for a while loop is as follows:

```bash
while [ condition ]; do
  # code to execute while condition is true
done
```

For example:
```bash
i=1
while [ $i -le 5 ]; do
  echo "Iteration $i"
  ((i++))
done
```


This will output "Iteration 1", "Iteration 2", "Iteration 3", "Iteration 4", and "Iteration 5".

## Functions
Functions allow you to define a block of code that can be reused multiple times in a script. Functions are useful for breaking up a large script into smaller, more manageable pieces.

To define a function in a bash script, use the following syntax:

```bash
function function_name {
  # code to execute
}
```

For example:

```bash
function greet {
  echo "Hello, World!"
}

greet
``` 

This will output "Hello, World!".

You can also pass arguments to a function and use them in the code. For example:


```bash
function greet {
  echo "Hello, $1!"
}

greet "John"
```

This will output "Hello, John!".

# Bash script examples
Now that you have a basic understanding of bash scripting, let's look at some examples of how it can be used to automate tasks.

## Example 1: Backup script
In this example, we will create a script that backs up a directory to a remote location using rsync.

First, let's define some variables to store the source and destination directories:

```bash
src="/path/to/source/directory"
dst="/path/to/destination/directory"
```

Next, let's define a function to perform the backup:

```bash
function backup {
  rsync -avz $src $dst
}
```
Finally, let's add a loop to perform the backup every hour:
```bash
while true; do
  backup
  sleep 3600 # Sleep for 3600 seconds (1 hour)
done
```
This script will run indefinitely, performing a backup every hour. You can stop the script by pressing Ctrl+C.

## Example 2: Disk usage script
In this example, we will create a script that displays the disk usage of a directory in a human-readable format.

First, let's define a function to display the disk usage:

```bash
function du_hr {
  du -sh $1
}
```

Next, let's ask the user for the directory to check and store it in a variable:

```bash
read -p "Enter the directory to check: " dir
```

Finally, let's call the function and pass the directory as an argument:

```bash
du_hr $dir
```

This script will ask the user for a directory and then display the disk usage in a human-readable format.

Conclusion
In this tutorial, we covered the basics of bash scripting, including the syntax and common commands. We also looked at more advanced topics such as loops, functions, and variables. By the end of this tutorial, you should have a solid foundation in bash scripting and be able to write your own scripts to automate tasks and improve your workflow.

Bash scripting is a powerful and widely used tool, and it is a valuable skill for any system administrator or developer. We hope this tutorial has helped you get started with bash scripting and that you will continue to learn and improve your skills.
