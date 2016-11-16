# Practice

## Before you get started

- You can access a documentation page about a specific command from the terminal
- Google lies. You can and must ask any question directly to Nicolas or the person sitting next to you. If they are not available, write it down, move on to the next topic and ask again before heading out of the practice session.
- Remember that everything you do on these machines will be lost by the time you log out of the Guest session. Write down anything useful.

## Creating a workspace

> Navigate to your home directory `~` with the `cd` command and create a directory named `bash-practice` with the command `mkdir`. Make sure the folder was created using the `ls` command.
> Now navigate to `bash-practice`.

## Basic programs


> Perform the following actions in the shell by using the `man` pages for any of the following commands `ls`, `touch`, `ln`, `cat`, `nano`, `ps`, `alias`, `rm`
> Write down each command on paper as you move through the tasks.

1. List all files in your user's directory, including hidden files.
- List all files in the `/` directory sorted by last modification time (one file per line). Notice which folders seem to be updated frequently and which haven't been updated for a long time.
- Show the content of the `~/.bashrc` file
- Create an empty file named `remove-me` (do not use `nano`)
- Add content to that file (within the terminal)
- Remove the previously created file. Use extra care with this command as it won't ask for comfirmation by default.
- Create an alias to the previously used command so that it asks confirmation before removing a file. Try that on a specifically created file.
- Create two directories `code` and `javascript` using one command, so that the relative path of the `javascript` directory is `~/code/javascript/`.
- Create a symbolic link from `~/js` to `~/code/javascript`
- Show a list of all running processes on your system. Display the results as a tree.


## The pipe operator `|`

> The pipe operator `|` allows you to redirect the output of one program as the input of another. For example ls
> With that in mind, perform the following action in one command.

1. Display a list of the 10 last commands you have run in this terminal
- Filter the history to display only unique lines
- Think of 3 other uses of the pipe operator


Hints: relevant commands possibly include `head`,`tail`,`cat`,`history`,`grep` and potentially others...

## Done? Find someone in the room you can teach something to.

## Done? Find someone in the room you can learn something from.
