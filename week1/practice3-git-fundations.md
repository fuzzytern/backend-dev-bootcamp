HELP FOR PART.I
===============

> Note: Just jump ahead to PART.I. This section aims to be used as a reference to come back to when you are stuck.

## Basic git workfow 

Note: as long as you are not confidently understanding what git does with the following commands, always run `git status` right after running EACH of them. Also run `git log` after each commit to see how the commit history is affected.

1. `git init repo_name; cd repo_name` <- Initialize an empty repository then move into it.
* Create and work on a file (e.g. `nano README.md`)
* `git add README.md` <- Add README.md to the staging area
* `git commit -m "Add README.md"` <- Moves staged changes (in that case adding README.md from the staging area to the commit area)

```
------------                  ------------                          ------------  
|          |                  |          |                          |          |
| UNSTAGED |                  |  STAGED  |                          |  COMMIT  |
|   AREA   | = git add ... => |   AREA   | = git commit -m "..." => |   AREA   |
|          |                  |          |                          |          |
|__________|                  |__________|                          |__________|
```

## Adding branches

1. `git checkout -b relevant_branch_name`
* Work on more stuff (e.g. Add more files, modify your existing README.md file...)
* Add and commit your work. If you added/modified several files you can use `git add -A` as well as relative paths to add a bunch (or all) files to the staging area in one go.
* To come back to the initial branch `master` use `git checkout master`

## Aliases

> Git, just like bash, support aliases. We're going to use the following one for this workshop:

`git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"`

> To use it, use `git lg`. This will display similar information than `git log` in a more compact and informative format.

## Working with remotes

> Working with remotes allow you to push work from your *commit area* on your local computer to a remote server.

```
------------                     ------------                        
|          |                     |          |
|  COMMIT  |                     | UPSTREAM |
|   AREA   | == git push ... ==> |  SERVER  |
|          |                     |          |
|__________|                     |__________|
```

1. Create a repository on [Github](http://github.com). Create an account if you haven't already.
* `git remote add origin <url>` <- `<url>` should be replaced by whatever URL Github gave you. 
* `git push --set-upstream origin master`


Note: You can add multiple remote sources to your local repository. This is useful when dealing with Forks (e.g. via Github). `origin` is just a name and could be anything. However it is de-facto convention that we use `origin` for the place we push to most of the time (our *fork*), and `upstream` for the origin repository we forked from. We will cover forking and authoring pull-requests in a later workshop.

Practice
========

## PART.I - Keeping it simple

To keep our attention on the tool itself, we will use only empty files in this part. Unless otherwise specified, a change will always consist in using `touch file<A-Z>` where `<A-Z>` will be relaced by `A` for the first file you create, `B` for the second etc...

Note: If you bring yourself to a state that doesn't correspond to the graphs and don't know how to undo that, call Nicolas.

0. Initialize an empty repository.
* Bring your commit history to the following state

    ```
    master: C1-C2
    mybranch:    `C3-C4
    ```
* Now bring it to the following state:

    ```
    master: C1-C2-------C5
    mybranch:    `C3-C4----C6
    ```
* Merge `mybranch` into `master`. Your history should now look like this:

    ```
    master: C1-C2-------C5----C7
    mybranch:    `C3-C4----C6-/
    ```
* Push this to your personal Github account (create one if needed). You will need to add a remote (see help section) pointing to a newly created repository on Github. 


## PART II - Improving your Git workflow

1. Use `man git-reset` then practice it on the `mybranch` branch of your previous repository.
* Learn how to rebase to perform flat merges from `man git-rebase`. Practice it on the repository of PART.I. You will need to `git reset --hard HEAD~1` on branch `master` to undo the last commit (merge commit). 
* Fork an existing repository of your choice from `iteratehackerspace` and perform a change you think meaningful. An easy change could be fixing a typppo in this lecture markdown file. Work in a separate branch of your repo, then push it to your upstream repository.
* Before you can submit your work for review to the `upstream` repository, you should make sure no change occured there. Use `git remote add upstream ...` to add the url of the repository you forked from. Then use `git fetch upstream`. This command will print out any change that occured since the last changes you got for `upstream` (at fork time at this stage).
* If you get anything new from the above command, you will need to perform `git rebase ...`. Call Nicolas in case of doubts.
* Once you think your work is ready for review, create a « Pull Request » via Github.

Resources
=========

1. [EASY win in case you're lost](https://www.youtube.com/watch?v=vR-y_2zWrIE&list=PLWKjhJtqVAbkFiqHnNaxpOPhh9tSWMXIF)
* [The Git user manual](http://git-scm.org)
* [The iteratehackerspace Github page](https://github.com/iteratehackerspace)
