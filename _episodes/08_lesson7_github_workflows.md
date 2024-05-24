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

It is also helpful to group our commits into logical self-contained updates.
This further increases the usefulness of the commit messages when reviewing the history.

See [A Note About Git Commit Messages](https://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html).

### Creating Pull Requests

The first workflow we are going to look at it creating a **pull request**, or **PR**.
In pure git this would be equivalent to asking someone to `git pull` the changes from your copy of their repository.
Since this is such a common action for collaboration, GitHub allows you to go through this process in the user interface.

We can create a *pull request* between any two branches.
In this example, we will look at creating a pull request from a **forked** copy of a repository into the original repository.

If we want to contribute to someone else's repository, we don't usually have write access, and hence we cannot push to it.
Instead, we shall create a **fork** of the repository through the button on GitHub, at the top of a repository we want to work on.

Try this now with <https://github.com/stephenpcook/intermediate-version-control>.

This will result a copy of the repository and its history with repository permissions associated with our user account.
As such, we will be free to create branches on GitHub to upload our changes, before requesting the original author to use them.

To work on the files, `clone` the repository to your local machine.
Navigate to your forked repository on GitHub, from the green **Code** button copy the `https` URL, then clone from your terminal

``` sh
git clone <https-url>
```

Next, follow the working patterns from the previous session to upload a new branch with some changes, i.e.,

- Create a new branch: `git branch my-changes`
- Switch to this branch: `git switch my-changes`
- Make changes to a file (such as fixing a typo in lessen 7) then commit: `git add <file>`, `git commit -m "Fix typo in lesson 7"`
- Finally, push your branch to *your* remote repository: `git push -u origin my-changes`

Once we have verified that we can see the changes on a new branch in our fork, we are ready to create a pull request.
For the repository in the above example, this can be found at <https://github.com/stephenpcook/intermediate-version-control/pulls>.

A notification will then be sent to the author of the repository.
The pull request page allows for comments, discussion, and lets the maintainer ultimately accept or reject the request.

This will be demonstrated in the session.

#### Exercise: Pull Requests

In pairs or small groups, practice making forks and Pull Requests on each-others' repositories.

#### Repositories with Collaborators and Teams

When working with colleagues, you are more likely to have some degree of access to the original repository.
In this case (depending on the repository settings) we should be able to directly upload changes to this remote, and wont need to create a fork.
We can still use pull requests from our branches to request to have our changes reviewed before arriving on `main`.

Permissions can be set up to impose limits on different users, such as restricting who can push to `main` without an approved pull request.

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
