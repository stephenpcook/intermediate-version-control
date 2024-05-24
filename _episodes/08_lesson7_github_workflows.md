---
layout: page
title: Remotes - GitHub
order: 8
session: 2
length: 45
toc: true
adapted: false
---

## GitHub Workflows

In this lesson, we will go through some examples of typical workflows for collaborating with GitHub.
The vast majority of the examples will directly translate to other hosting platforms, such as <https://bitbucket.org/> or <https://git.exeter.ac.uk/>.

The lesson will take the form of short demonstrations, followed by time to practice the workflow with you course mates.

### Aside: Good Commit Messages

When working collaboratively it is a good idea to adopt common conventions.
A **strong** recommendation is to use a consistent format for commit messages.
Having this consistency makes the workflows presented here, as well as the `log` and `blame` most effective.

The first line of the commit message should be a short summary, written in the imperative, of *what this commit will do if applied*.
This title is what will show up in the one-line version of our history, and should be capitalised without punctuation.
It can be equated to the subject of an e-mail.
Some examples are:

- Update text on commit messages in workflow lesson
- Fix missing dependency
- Add links to each lesson in the schedule

If further information would help describe the reasons for the commit, it can optionally be added to the body of the commit.
This text should be separated from the title by a single blank line and ideally wrapped to 72 characters.
GitHub allows for references to *issues* and *pull requests*, as we shall see below.

An full example of a commit message:

``` none
Update text on commit messages in workflow lesson

This serves as an example of good commit messages and will serve as a
prompt to use good commit messages for the exercises in the lesson.

It includes:

- a summary of best practice
- an example commit message
- a link to a post
```

See [A Note About Git Commit Messages](https://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html).

### Creating Pull Requests from a Fork

TODO:

### Creating Issues and Linked Pull Requests

TODO:

### Reviewing Pull Requests

TODO:

### Summary

We have seen how to work with remote repositories, and how download and upload changes.

In the next remainder of this session we will look at typical workflows using GitHub.
We'll also see how we can rewrite our history, as well as the tools we have available to get unstuck when applying these more complicated changes.

### Exercise

We will go through an example of creating our own fork of a public repository, cloning our own version of it, then adding an upstream remote to the original repository.
