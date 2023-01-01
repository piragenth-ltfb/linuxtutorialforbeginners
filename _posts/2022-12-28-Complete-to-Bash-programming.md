---
Author: Piragenth
Title: Beginner's Guide to bash programming | The Complete Beginner's Guide
Date: 2022-12-28T14:56:35 + 05:30
draft: false
category:
- bash
- Linux
tags:
- bash
- linux
---

![](https://linuxtutorialforbeginners.com/assets/Pictures/bash-script.png)

Welcome to this comprehensive guide to scripting! bash Script is a powerful tool to automate tasks and make them more efficient. This is widely used in the world of Linux Ubuntu and Unix and can be a useful skill for any system administrator or developer.

In this guide, we'll cover everything you need to know to get started with bash scripting. We begin by introducing the basics of bash scripting, including syntax and common commands. Then we move on to more advanced topics like loops, functions, and variables. By the end of this tutorial, you will have a solid foundation in scripting and be able to write your own scripts to automate tasks and improve your workflow.

Before we get into the tutorial, let's explain what a master script is and how it works.

# What is the main script?

bash scripting is the method of writing scripts or programs using the bash shell, which is the default shell on many Linux and Unix systems. A shell is a command line interface (CLI) that allows users to interact with the operating system by typing commands and executing scripts.

The bash script is written in a text file and saved with the extension .sh. It can be run from the command line by typing "bash script.sh" or by executing the script using "./script.sh".

bash scripts can perform a variety of tasks, from simple tasks such as displaying messages on the screen to complex tasks such as automatic backups or server deployments.

# Do you need to learn scripting?


There are several reasons why you might want to learn bash script:

* A versatile and powerful tool. It is the default shell on most Linux and Unix systems and is used by system administrators and developers around the world. Knowing how to write a bash script will make you a more valuable and versatile employee or freelancer.
* It can save your time and energy. bash scripts allow you to automate tasks and reduce the amount of work you do. This can save a lot of time and energy, especially if you have to do the same task over and over again.
* Easy to learn. Basic scripting is easier to learn, especially if you already have programming experience. The syntax is simple and straightforward, and there are plenty of resources to help you learn.

# Start with the main script
Before you can start writing scripts, you need to have a Shell on your system. If you're using a Linux or Unix system, you probably already have bash installed. If you are using Windows, you can download and install Windows Subsystem for Linux (WSL).

After you install the basher, you can write the basher script by creating a text file and saving it with the extension .sh. You can use any text editor to create the script, such as vi, emacs, or a simple text editor such as Notepad.

To run a bash script, you can run it from the command line by typing "bash script.sh" or you can run it using the chmod command and run it with "./script.sh".
Here's a simple example of a basher script that displays a message on the screen:

``bash
#! / bin / bash
or "Hello, World!"
``

To run this script, save it as salam.sh and execute it with the following command:

``bash
Hello.sh
``
"Hello World!" You should see the message. displayed on the screen.

# bash
## Main script syntax
Now that you know how to create and run basher scripts, let's look at the syntax and some common commands used in basher scripts.

## Comment
You can add comments using the "#" symbol in the basher script. Comments are used to explain what the script does or to add notes for yourself or others. Anything after the "#" character in the string is treated as a comment and the script is ignored.

For example:

``bash
# This is a comment
or "Hello, World!" # This is also a comment
``
## Variables
You can use variables to store and manipulate data in the main script. Variables are denoted by a dollar sign ($) and can contain numbers, strings, or arrays.

To assign a value to a variable, use this syntax:

``bash
var_name = value
``
For example:

``bash
name = "john"
age = 30
``

To use a variable in a script, use a dollar sign with the variable name:

``bash
echo "My name is $name and I am $age."
``
Main script syntax
Now that you know how to create and run basher scripts, let's look at the syntax and some common commands used in basher scripts.

commentary
You can add comments using the "#" symbol in the basher script. Comments are used to explain what the script does or to add notes for yourself or others. Anything after the "#" character in the string is treated as a comment and the script is ignored.

For example:

``bash
# This is a comment
or "Hello, World!" # This is also a comment
``
VARIABLE
You can use variables to store and manipulate data in the main script. Variables are denoted by a dollar sign ($) and can contain numbers, strings, or arrays.

To assign a value to a variable, use this syntax:

``bash
var_name = value
``
For example:

``bash
name = "John"
age = 30
``
To use a variable in a script, use a dollar sign with the variable name:

``bash
echo "My name is $name and I am $age."
``
It will come out "My name is John and I'm 30 years old."

You can use variables in arithmetic operations by enclosing them in a double shell:

``bash
((result = 5 + 3))
echo "Result $ result."
``
This will output "Result 8".

## Command

You can use commands to perform actions or manipulate data in the parent script. There are many built-in commands, such as the echo used in the previous example, to display messages on the home screen.

To use a command in the main script, type the command followed by an argument or option. For example:

``bash
or "Hello, World!" # Display the message on the screen
ls -l # Display the contents of the current directory in long format
``

You can also use external commands or programs in your main script by specifying the full path of the executable file. For example:

``bash
/usr/bin/python my_script.py # Execute the Python script
``

# Condition
Conditions allow you to execute different commands or blocks of code based on specific conditions. In the parent script, you can use an if statement to execute a block of code if the condition is true.

The syntax of the if statement is as follows:


``bash
if [condition]; later
  # code to execute if the condition is true
other
  # code to execute if the condition is false
fi
``

For example:

``bash
age = 20

if [$age -gt 18]; later
  or "You will grow up"
other
  or "You are under age"
fi
``

It will come out "You will grow".

You can also use an ellipsis clause to specify additional conditions to be checked. For example:

``bash
age = 17
if [$age -gt 18]; later
  or "You will grow up"
elif [$age -gt 12]; later
  echo "You're a teenager."
other
  or "You Baby"
fi
``

## Circuit

Loops allow you to execute a block of code multiple times. In the main script, you can use it in a loop to execute blocks of code based on specific conditions.

The syntax for a loop is as follows:

``bash
as listed; meat
  # code to execute each element in the list
finished
``

For example:

``bash
1 2 3 4 5 for me; meat
  echo "Iteration $i"
finished
``

This will produce "Iteration 1", "Iteration 2", "Iteration 3", "Iteration 4" and "Iteration 5".

The syntax for a bit loop is as follows:

``bash
[state]; meat
  # code to execute if the condition is true
finished
``

For example:
``bash
i = 1
[$i-le 5]; meat
  echo "Iteration $i"
  ((i++))
finished
``


This will produce "Iteration 1", "Iteration 2", "Iteration 3", "Iteration 4" and "Iteration 5".

## Functions
Functions allow you to define a set of code that can be reused multiple times in a script. A useful function to break a large character into smaller, more manageable chunks.

Use the following syntax to define functions in the main script:

``bash
function_name {
  # code to execute
}
``

For example:

``bash
function hello {
  or "Hello, World!"
}

Hello
``

It's a "Hello, World!" It will come out.

You can also pass arguments to functions and use them in code. For example:


``bash
function hello {
  or "Hi, $1!"
}

hi john
``

Here's a "Hi, John!" It will come out.

# Example of the bash script
Now that you have a basic understanding of bash scripting, let's look at some examples that you can use to automate tasks.

## Example 1: Custom script
In this example, we will create a script that backs up a folder to a remote location using rsync.

First, let's define some variables to hold the source and destination directories:

``bash
src = "/path/to/source/directory"
dst = "/path/to/destination/directory"
``

Next, define a function to perform a backup:

``bash
function backup {
  rsync -avz $src $dst
}
``
Finally, add a loop to do the backup every hour:
``bash
if true; meat
  backup copy
  sleep 3600 # Sleep 3600 seconds (1 hour)
finished
``
This script will run for some time and perform backups every hour. You can save the script by pressing Ctrl + C.

## Example 2: Disk usage script
In this example, we will create a script that displays directory usage in a human-readable format.

First, let's define a function to display disk usage:

``bash
du_hr function
  du-sh $1
}
``

Next, ask the user to verify and save the directory to a variable:

``bash
ok -p is "Enter directory to check:".
``

Finally, let's call the function and pass the directory as an argument:

``bash
du_hr is $
``

This script will prompt the user for a directory and then display the disk usage in human readable form.

The results
In this tutorial, we've covered the basics of bash scripting, including syntax and common commands. We also look at more advanced topics like loops, functions, and variables. By the end of this tutorial, you should have a solid foundation in scripting and be able to write your own scripts to automate tasks and improve your workflow.

bash Scripting is a powerful and widely used tool and valuable skill for any system administrator or developer. We hope this guide will help you get started with basic scripting and that you will continue to learn and develop your skills.