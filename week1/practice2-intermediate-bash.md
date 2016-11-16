# Before you get started

## Useful bash-every-day tips

- Use and abuse autocompletion. The `[Tab]` key will autocomplete your commands.
- To get a short description about what a specific program does use `whatis <program>`
- To get a detailed manual for a specific program use `man <program>` for help with bash scripting 
- The `info <program>` command will prompt an insightful user guide for the specified program. This goes into much lengthier explanations than a man page. 
- `man` itself has a man page (`man man`), and looking into it WILL help you use `man` more effectively
- You use `apropos <expression>` to get a list of programs dealing with a specific topic. `apropos` can take a section number (e.g. `apropos -s1 count`). The following excerpt form the `man man` page describing is especially useful to know how to use sections properly depending on what you are looking for.

> The table below shows the section numbers of the manual followed by the types of pages they contain.
>
> 1.  Executable programs or shell commands
> *   System calls (functions provided by the kernel)
> *   Library calls (functions within program libraries)
> *   Special files (usually found in /dev)
> *   File formats and conventions eg /etc/passwd
> *   Games
> *   Miscellaneous  (including  macro  packages and conventions), e.g. man(7), groff(7)
> *   System administration commands (usually only for root)
> *   Kernel routines [Non standard]

# Practice

## New tools

> Use the command `apropos`, to find out which command to use for the following operations:
> Hint: Only the « Executable programs or shell commands » sections is relevant for us.

1. compare two files line by line
* suspend execution for a specific amount of time
* print the count of newlines of a given file
* outputs the standard input to the standard output while also writing it to a file

## Output redirection

> By default the shell reads from the standard input, `stdin` and writes to the standart output, `stdout`. With the `|` (pipeline) operator (used last workshop), the output of the command to the left of the operator is redirected as input to the command to the right. Besides `|`, other operators are used to redirect output in the shell:
> - `>>` appends the output of the left operand to the file specified by the right operand.
> - `>` writes the output of the left operand to the file specified by the right operand. If that file already exists, its content will be overwritten (use care when using this).
> - `<` uses the file specified in the right operand as an input to the command in the left operand.


> Perform the following using the proper output redirection operator (`|`, `>`, `>>` or `<`):

1. count the number for files (or directories) in your home directory. Hint: one of the command should take the `-1` option (that's « one » not « L »)
* count how many environment variables are defined in the local environement
* append the line of text "Bash is so fun!" to the non-existent file named `no_lies`
* display your command line history in a pager
* list contents of the filesystem root in a tree-like format, inside a pager (and take a minute or two to see what's in there).
* write the content of the environment variable `PATH` into the file `current_path`. Use `cat` to verify the contents start with `PATH=/...`
* display the the number of lines of the file `no_lies`

## Useful script

> Create a bash script called `manpart` that uses the programs `man` and `less` to open a manpage directly at a specific subsection that it contains.
> For example `manpart less "OPTIONS"` will open a the documentation for `less` directly at the « OPTION » subsection, so you don't have to manually scroll/navigate through.



## Done? Find someone in the room you can teach something to. 

## Where to from here?

- In the `Output redirection` section, we didn't cover how to redirect `stderr`. By default these operators only manipulate the standard input and errors won't be redirected (e.g. `ls -xy > file` won't write anything to the file) notations such as `2>`, `2>&1` etc...
- `info bash`, is an insightful step-by-step user documentation covering all you should know about bash.
- Whatever your level with `bash`, you will learn a lot with [The Art of The Command Line](https://github.com/jlevy/the-art-of-command-line). Note this guide is [also available in Russian](https://github.com/jlevy/the-art-of-command-line/blob/master/README-ru.md)
