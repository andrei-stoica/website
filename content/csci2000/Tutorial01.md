+++
date = "2020-09-12"
title = "Tutorial 01 - Getting start with Jupyter Cloud and Linux"

+++

## 1. Getting to know Jupyter Cloud

When you first log in you will be asked to log in with your Google account.
Please log in with your @ontariotechu.net account.

![Jupyter Cloud Login](/csci2000/resources/tutorial01/login.png)


Then click the course code (csci2000) to go to your dashboard.

![Course code](/csci2000/resources/tutorial01/course-code.png)

Finaly click on 'Start My Server' and confirm by clicking 'Launch Server'


![Start server](/csci2000/resources/tutorial01/start-server.png) 
{{< center >}}
VVVVVVVV
{{< /center >}}
![Confirm](/csci2000/resources/tutorial01/confirm.png)


This may take a few moments. Especially if a lot of students are trying to
access Jupyter Cloud at the same time. Once you are done you should see the
main file browser.


![Main Window](/csci2000/resources/tutorial01/main.png)

From here we can:

 - Browse the file system
 - create and edit text files
 - create and edit Python3 notebooks
 - launch a terminal emulator

If we click 'New' in the top right we see the option to create new notebooks,
files, folders, or terminals. 


![New Dropdown](/csci2000/resources/tutorial01/new.png) 

Notebooks are where we can write code and execute it. This can be done in chunks
or cells. Writing spreading our code over multiple cells allows us to execute
them separately and verify the output of one chunk before we continue. We
can also modify and execute a cell again if we need to modify something. A cell
can can contain code or formatted text. You can format text using Markdown.
Using and formatting Notebooks will be discussed in greater detail in future
tutorials.

![Notebook](/csci2000/resources/tutorial01/notebook.png)

The terminal allows use to use a Bash shell to manage our instance and
manipulate files. This is far more powerful then a visual file manager at
working with multiple files at a time. From here we also have access to many
other useful commands for exploring, editing or finding files. As well as, 
looking at running and managing processes, checking disk and memory usage. A lot
of useful commands will be discussed in this weeks and next weeks tutorials.

![Terminal](/csci2000/resources/tutorial01/terminal.png)

Terminals and Notebooks will run in the background. To see what is still running
you can use the 'Running' tab from the main page. On this tab we can also 
shutdown any of the running Jupyter processes. 

![Running Tab](/csci2000/resources/tutorial01/running.png)


## 2. Getting started with the command line

When you start a new terminal in Jupyter Cloud, it spawns a Bash shell. Bash is
a very common Linux command line environment. A lot of what you'll learn here
will transfer to other Linux distributions such as Ubuntu, Fedora, or Arch. 
This tutorial only covers some of the basics but we will learn more about the
power of Bash and the Linux command line throughout the semester.

First we can check the current time and date with the `date` command:

![Date](/csci2000/resources/tutorial01/date.png)

`df` tells us our current disk usage:

![DF](/csci2000/resources/tutorial01/df.png)

`free` tells us our current memory usage:

![Free](/csci2000/resources/tutorial01/free.png)

If we want to rerun a previous command, we can use the arrow keys to navigate
our command history. UP goes backward and DOWN goes forward. 

Lastly, we can end a session with the command `exit`. Note: this does not close
the window but we cannot run any more commands

![Exit](/csci2000/resources/tutorial01/exit.png)

## 3. Navigating the file system

Let's discus the basics of navigating the file system in a command line
environment. We can't click or drag 'n drop files around but that doesn't mean
we can't do anything. As a matter of fact we have more powerful tools for
working with multiple files and doing task such as bulk renaming, or automating
repeated tasks. 


First let's get our bearings. `pwd` will let us know where we are located.

![PWD](/csci2000/resources/tutorial01/pwd.png)

As we can see, we are currently in `/home/jovyan`. We can now use `ls` to list
the files in this directory/folder.

![LS](/csci2000/resources/tutorial01/ls.png)

We can now see that this directory contains one thing: another directory called
'work'. We can use `cd` to change directories to this new directory. If we 
repeat the previous stop we can see that this directory is the same as the one
we can access through Jupyter Cloud's file browser. All work done with Jupyter
Cloud will be placed under this directory.

![CD](/csci2000/resources/tutorial01/cd.png)

We need to specify `cd` the path to the directory we want. In our example we wanted
`work`. This is a relative path, meaning relative to our current directory. So
the absolute path to the same directory would be `/home/jovyan/work/`. All
absolute paths start with `/` meaning the root (or top) of the file system. We
could have also supplied `cd` with an absolute path.

Similarly `ls` allows us to select which directory we want listed. By default
it will print the files in our present working directory (`pwd`) but if we
pass `/home/jovyan` as and argument we get a different output. If we wanted to
print multiple folders we can do that as well. Plus we can mix and match
absolute and relative paths.

![Listing multiple paths](/csci2000/resources/tutorial01/ls-paths.png)

There are also a few shortcuts we can use:

 - `-` 
  * the previous directory
	* similar to the back button in Windows File Explorer 
	* this is useful if we want to go back
 - `..` 
	* up one directory
  * similar to the up button in Windows File Explorer
 - `.`
	* the current directory
 - `~` 
  * our home folder
 - `~<user>`
  * the home folder of the specified user
	* ie `~jovyan` for our home folder

Most programs have a set of options and arguments that modify their behaviour.
Usually specified in the order `command -options arguments`. For `ls`, the
argument is the directory you want listed. There are also a number of very
useful options:


 Long Version      | Short Version | Description  
:-----------------:|:-------------:|-------------------------------------------------------------
 `--all`           | `-a`          | show all files, including hidden files
 `--directory`     | `-d`          | show detail about directory instead of contents
 `--classify`      | `-F`          | append indicator to end of name (displays file type)
 `--human-readable`| `-h`          | display file size in human readable format instead of bytes
                   | `-l`          | display in long format
 `--reverse`       | `-r`          | display in reverse alphabetical order
                   | `-S`          | sort by file size
                   | `-t`	         | sort by modification time


Note that some of these have both long and short versions. You can use either.

Let's take a look at the long format for `ls`:

![LS long listing](/csci2000/resources/tutorial01/ls-long.png)


 Field                 | Description
 :--------------------:|:-----------------------------------------------------------------
 `-rw-rw-r--`          | file type and permissions in order: type user(`rwx`) group(`rwx`) world(`rwx`)
 `1`                   | number of hard links to file
 `jovyan`              | username of owner
 `jovyan`              | name of group owner
 `834`                 | file size in bytes
 `Sep 13 18:01`        | timestamp of last modification
 `'Hello World.ipynb'` | file name

We can look at the contents of a file using the `less` command. If we use it
to look at the contents of a `.ipynb` file we will get something that looks
like this:


![less](/csci2000/resources/tutorial01/less.png)


You can navigate the file while in less. Here is a chart of the commands:

Command                     | Action
:--------------------------:|-----------------
`PAGE UP` or `b`            | scroll up one page
`PAGE DOWN` or `SPACEBAR`   | scroll down one page 
`UP ARROW`                  | scroll up one line 
`DOWN ARROW`                | scroll down one line 
`G`                         | go to end of file
`1G` or `g`                 | go to begining of file
`/<sequence>`               | search for next occurance of \<sequence\>
`n`                         | search for next occarance of previous search
`p`                         | search for next previous of previous search
`h`                         | display help
`q`                         | quit
