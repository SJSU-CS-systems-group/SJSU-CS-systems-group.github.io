---
layout: post
title: terminals and shells
---

# terminals and shells

when i first started using UNIX i was very confused by the term “shell”. in fairness, i find it to be a non-intuitive term! i was dialing up remote systems using my old MS-DOS machine, (yeah, i’m old.) but the concept of a shell seemed very foreign to me. in this blog, i’ll review some key concepts of terminals and shells that you need to understand to effectively use UNIX (mostly linux nowadays).

## terminal

my first internship during college i used a VT-52 terminal to access what was then brand new SUN machines.

![image of VT-52 terminal](https://upload.wikimedia.org/wikipedia/commons/1/1c/Terminal-dec-vt52.jpg)

this terminal allowed me to log onto the machine and use it. the terminal itself was pretty dumb. it would display whatever text (80 columns by 24 lines) the computer sent to it and it would transmit my key presses to the computer. the terminal itself didn’t do any processing.

today, we don’t use physical terminals; instead, we use terminal programs that create a window that we can use to give commands to the operating system. the terminal program’s job is the same as the physical terminal: it receives text to display from the operating system and sends any input it receives to the the operating system.


> :information_source: if you are a windows user, i’ve become a use fan of fluent terminal! it has a lot of great features and supports the normal windows command shell, powershell, and ubuntu.
> 
> for linux, i highly recommend konsole. (my dream is that someone ports konsole to windows!)

---

## the shell

actually, the terminal doesn’t talk directly to the operating system; it interacts with a shell. (whether the shell is considered part of the operating system is a much larger, mostly irrelevant, semantic argument.) a shell is another program that presents an interactive environment to a user. sometimes that “user” is a script, but we are focused on what happens when we use a shell.

when you start up a terminal and see a prompt, that prompt you see is coming from the shell.

![shell with ls command](/assets/shell.png)

shells have evolved over time. on my first computer the shell was a BASIC interpreter. you can even use python as a shell if you would like, but most shells today resemble the original bourne shell. in these shells you issue commands with parameters (AKA arguments) separated by spaces. make sure to use quotes if you want to have parameters with spaces   some commands will be interpreted directly by the shell, but many, like the ls command in the example, will be other programs that the shell will run for you.

on a modern computer, when you open a terminal program, you are actually running two programs: 1) the terminal program which is managing the display and input and 2) a shell program that provides you an interactive environment to tell the operating system to do things. each time you open a tab in the terminal program or open a new terminal window, you start a new shell program running.

i’ve been a huge fan of bash (the bourne again shell). it is the default shell on most systems and for a long time on OSX, but in apple’s quest to avoid GNU licensing obligations, they have switched the zsh. it turns out that zsh is pretty awesome as well. it is mostly the same as bash, but with a bit of extra awesomeness. (floating point number support is a big deal to me!)

## ssh

its cool to do stuff on your own computer, but we live in the internet age. cool kids are actually using many computers. a common way of accessing other computers over the internet is ssh (secure shell). ssh will connect to a remote computer and start a shell on it. in the process of setting up the connection, it will use various encryption and authentication protocols to make the connection “secure”. the job of ssh is simple: shuttle data to and from the remote shell over the network connection. the terminal program will render the data locally and collect data to send, and the remote shell program running on the remote server will take care of executing the commands it gets.

so there you have it! we have a terminal program that will give us a user interface to work with, a shell to run commands with, and ssh to run commands remotely. that is everything we need . need yes! but want? NO! we want more!

---
**NOTE**

you aren’t fully using ssh unless you have set up a private key pair, authorized_keys, and an ssh-agent. getting those things set up will make your life so so much easier!

---

## tmux

the mobility of our computers causes problems for ssh. when we change networks or suspend and resume or reboot our routers, the network setup changes and we lose our ssh connection. while it’s not the end of the world to reconnect with ssh, sometimes we have experiments running or editors open. sometimes we have an elaborate remote set of screens open on the remote machine that we would like to avoid losing.

this is were tmux comes in. tmux allows you to create a remote terminal that will stay running even if you lose your network connection. when you reconnect to the remote machine, you can attach to that terminal and resume where you left off. of course tmux has a lot more than just session preservation. it will also manage scrolling for you, allow you to create many remote virtual terminal buffers and windows that you can switch between or tile. many programmers never use or master tmux, but those who do impress their peers with both their environment and their productivity.

---
**NOTE**

screen was the precursor to tmux. it used to be the fall back if tmux wasn’t available, but tmux is pretty ubiquitous these days.

---

understanding and using terminals, shells, ssh, and tmux effectively will allow you to be more productive in your work, but it doesn’t stop here. ssh has some really awesome tunneling features that can make you look like a network wizard. programs such as eternal terminal and mosh can make changing networks even more seamless. to really understand and become effective with these tools, you need to use them! providers such as oracle cloud and IBM cloud among others provide free remote virtual machines that can give you a chance to get experience.
