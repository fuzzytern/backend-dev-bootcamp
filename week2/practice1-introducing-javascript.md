REFERENCE
=========

Note: This section is to assist you with using intermediate git concept in this workshop. If you haven't done so already, [jump ahead](#collaborative-coding) to the practice directly, and come back here as needed.

## Forking

The concept of forking on Github (and other git-based plaftorms) allows you to copy one repository from one place to another. It can be used:

- If you want to contribute to a repository you do not have ownership on. In this case you will work on your own copy (fork), then submit a *Pull Request* when you're ready to show off your work to the maintainer of the original repository.

## Squashing your commits

Before merging your feature branch into `master`, it can be a good idea to squash multiple commits into one. This helps keep the commit history clean as you might (and should) have worked on small iterations on your feature branch. The idea is to have only one meaningful commit describing the work that you have been doing to avoid clutter.

To squash all your commits into one use:

```
git rebase -i #commit-id
```
Where `#commit-id` is replaced by the commit reference of the commit preceding the last one you want to squash. 
This will open a text editor with text in it. Read all of it attentively, then use `squash` where apprioriate.

## Rebasing

Before you merge your feature branch into an upstream one, it is a good practice to perform a rebase. The command:

`git rebase upstream/master`

Will do the following:

1. put all commits you performed after branching aside
* update your branch with any change that has hapened on `upstream/master` since the time you branched out
* replay your work (commits) on top of it.

This practice ensures that the commit history of `upstream/master` will be flat (thus readable).


COLLABORATIVE CODING
====================

In this section you will work on the [iteratehackerspace/ecmascript-sandbox](https://github.com/iteratehackerspace/ecmascript-sandbox) repository. It will help you learn, write, feedback and refactor javascript code samples demonstrating different features of the language. We (and external contributors) will keep using and updating this repository through our journey of learning Javascript. Take a moment now to visit it and read the README.md.

Done reading? Good. Now, you're going to work in pairs. Team up then do the following:

0. Choose one person of you who will **fork** the iteratehackerspace/ecmascript-blocks. That person should give access to their collaborator to their own fork.
* Once given access, clone the forked repository on both of your machines.
* Write one code example each. Your code example should be related to the [Grammar and types](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Grammar_and_types) chapter of the MDN guide. Take a moment to skim through some of that page before writing your code (you don't need to understand all of it). You might feel  unconfident to write any javascript code just yet. That's fine, try some sample from that page in your browser javascript console and come back to writing code once you've learned something from that.
* Once you have some kind of javascript example, commit and push it to the fork.
* Wait that your partner has done the same, then pull their work to review it. Try their code in `node` or the browser console and think of any possible improvements.
* Once both of you reviewed each-other's examples, give feedback about them (face-to-face here), and decide which of them you should keep to turn into a problem.
* Use pair-programming (sitting both on the same computer, one writing, the other commenting) to refactor the example you chose, and add instructions for the problem you are creating.
* Once you're proud of the problem both of you worked on, make a pull-request to the upstream repository. You should run `git rebase upstream/master` in your branch before doing so, make sure there is not conflict and that the command succeeds.
