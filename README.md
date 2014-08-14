Bash Tutorial
=============

_Bash_ is a UNIX shell.  A _shell_ is a command processor, it waits for commands you type in, runs them and prints out the results.  A _command_ is a (typically simple) program with text input and output that does something, for example shows information about a file, or fetches a web page.

In this tutorial, _terms_ that are defined are shown in italics, and __commands__ that you can run are shown in bold.  When you run a command and it prints some output, it is shown in a box, like this:

    $ command 
    output 

Run all the commands in the examples.  It is safe; you can't break anything.

# Getting started

Run a terminal.  This usually has an icon with an empty computer monitor, on Ubuntu it looks like an empty monitor with >_ displayed in it.

Once the terminal runs, you will see a prompt.  A _prompt_ is what the shell prints to let you know it is ready for commands.  The typical prompt is "$", although sometimes it might be something like "username@computer $".  There is usually a blinking cursor after the prompt to let you know the terminal is ready to type in as well.   

Type a command after the prompt and press "Enter" or "Return" to run it.  It will run, and then you will see the prompt again.

Try running a command at the prompt now:

    $ pwd
    /home/alex

The __pwd__ command prints the working directory.  

A _directory_ is like a folder in Windows, it contains files and other directories.  Directory and file names are separated by "/" so what this command told us is that the working directory is "alex" inside "home" (this may be different for you).  

The _working directory_ is where we are at the moment; it is like the currently open folder in Windows.  Many things use the working directory by default.  It is common to talk about being "in" the working directory.

A complete description of where a directory or file is located is called a _path_, for example "/home/alex".

Command names are often a useful reminder of what the command does, for example by abbreviating a description of the command, __pwd__ for print working directory.


# Getting around

Let's try changing the working directory:  

    $ cd /home
    $ pwd
    /home

## Arguments

The __cd__ command changes the working directory.  However, we need to tell it what directory to change to: to do that, we used an _argument_.  An _argument_ is some text after the command that tells it what to do, in this case what directory to change to.  Here __cd__ is the command and "/home" is the argument.  Some commands can have more than one argument.

The __cd__ command did its job but didn't print anything afterwards; to check that it worked we ran __pwd__ again.  Often, commands don't print anything unless they run into an error.

Let's go back to the directory we used to be in:

    $ cd /home/alex
    $ pwd
    /home/alex

Let's see what files and directories are in this directory:

    $ ls
    ... list of files here

The __ls__ command lists files and directories.  It can take any number of arguments of which files and directories to list.  For example:

    $ ls /home
    alex/
    ... list of other files and directories here

## Options

If we want more information, we can call __ls__ like this:

    $ ls -l
    ... list of files and directories with extra information like size and modification time

The part "-l" after the command is an _option_.  An _option_ is a modifier that tells the command to do things in a slightly different way, in this case display a list in "long" format.  Options are similar to arguments but they tell a command how to do what it does, instead of what to work on.  

Let's run __ls__ again with a different option:

    $ ls --all
    ... list of files and directories

Here "--all" is a _long option_.  This particular long option shows all files, including some files which are normally hidden.  Options can start with a dash or double dash.  Single-dash options are (usually) just one letter, but double-dash _long options_ can be words.

Options can be combined:

    $ ls -l --all

Arguments and options can also be combined:

    $ ls -l --all /home


# Making things

Let's make a directory:

    $ mkdir test_directory
    $ ls
    test_directory
    ... list of other files and directories here

The __mkdir__ command makes a directory. It takes an argument to tell it what directory name or path to create.

Let's go to the directory we just made:

    $ cd test_directory
    $ pwd
    /home/alex/test_directory

Let's make some empty files:

    $ touch test_file_1
    $ touch test_file_2
    $ touch another_test_file
    $ ls
    another_test_file  test_file_1  test_file_2

The __touch__ command makes an empty file if it doesn't already exist.

When we made a directory and files here, we just gave their names, and they were created in the working directory at the time.  We could also give a full path to create them anywhere:

    $ touch /home/alex/test_file_3
    $ ls /home/alex/test_file_3
    /home/alex/test_file_3
    $ pwd
    /home/alex/test_directory
  
By giving a path instead of just a name, we created a file that is not in the working directory we were in.  Yay!

## Commands that don't exit immediately

Let's look at the contents of one of the files we made:

    $ less test_file_1
    test_file_1 (END)
    ... now press q
    $

__less__ is a command that shows the content of a file one page at a time.  This file is empty, so there is nothing to see :)  If there was a lot of text, you can press space to go to the next page, or "q" to quit.  You can also use up and down arrows or up and down page to move around.  This is an example of a command that doesn't finish right away; it stays running (and takes input) until you ask it to quit.

Now, here is another way to force a command to exit:

    $ less test_file_1
    test_file_1 (END)
    ... now press Ctrl and c keys at the same time
    $

This forces the currently running command to exit.  This is useful for commands that are not polite about exiting when requested, for example commands that should finish immediately (and don't wait for a prompt like __less__), but unexpectedly take a longer time to run.

# Moving things around

TODO

# Working with groups of files

The shell has a powerful way of working with files based on patterns in their names.  Let's use that to list several files at once:

    $ ls test*
    test_file_1  test_file_2

This asks __ls__ to list any files whose names start with "test".  The way to read the "\*" is "anything", so the pattern is "test" followed by "anything".  "\*" is called a _wildcard_ because it matches anything just like a wilcard does in card games.  

Note that the file "another_test_file" we created earlier is not included, because its name doesn't start with "test".  

If we want all files that have "test" anywhere in the name:

    $ ls *test*
    another_test_file  test_file_1  test_file_2

Let's try a few more.

    $ ls *1
    test_file_1

Wildcards can be used in paths as well as names, and they can be used more than once:

    $ ls /home/alex/test*/test*
    /home/alex/test_directory/test_file_1  /home/alex/test_directory/test_file_2



# Interlude: why use the shell?

Coming from a graphical user interface, the shell may at first seem like a complicated way to do things that you can just do by clicking around folders and files.  The real power of the shell is in its ability to build very powerful sequences of actions by putting together simple commands as building blocks.  In Windows, you might (for example) search for any pictures you have saved in the past month.  In UNIX, you might search for any pictures you have saved in the past month *and* make them smaller *and* upload them to flickr.com, all in one shot.

 
# Cookbook recipe: do something to a bunch of files

TODO

