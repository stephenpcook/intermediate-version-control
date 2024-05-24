---
layout: page
title: Rewriting the History
order: 9
session: 2
length: 20
toc: true
adapted: false
---

## Rewriting the History

In previous lessons we have seen how to create commits, branch our work and merge changes from multiple branches.
In this lesson we going to look at the options we have available to rewrite the commits in our history.

When changing the history, we can lose sight of commits, so these operations aren't completely without risk and some care must be taken.
We'll cover some precautions to take, and also see how to recover from mistakes.

### When to Rewrite the History

As a rule of thumb, don't rewrite any history on a `main` branch.
For a more nuanced approach, the more people who have a version of a commit, the less inclined you should be to rewrite the history.
The safest time to rewrite the history is on a local branch that hasn't made it to a remote repository.

Once a tracked branch has been pushed to a repository, if we modify the history the try to re-push, we will get an error message.
We can tell the remote to replace the commits with the ones we are supplying with the `--force` argument, if we're sure this is what we want to do.

### Getting Unstuck

In all the cases presented below, making changes to the commit will actually create new commits with new SHAs.
If the previous commit have no references pointing towards them (branches, tags, remote branches or detached HEAD) then they will no longer show up in our `log` (even with the `--all` flag).

These *dangling commits* are still reachable from their SHA, but it is possible they could be cleaned up at some point by git's garbage collector.
If you perform an operation here and lose a commit you wanted (step 1, Don't Panic), you can still see and reach the most recent commits visited:


``` sh
git reflog
```

These commit can either be access by the SHA, or the special references, e.g., `HEAD@{1}` for the previous commit location.
In the first instance, it would be best to attach a branch or tag to the chain of misplaced commits (e.g., `git tag whoops HEAD@{1}` or `git branch whoopsy HEAD@{1}`).
Following this you will be at your leisure to search the internet for how to recover your previous state (typically involving `git reset`).

### Amend Commit

The smallest (and arguably safest if done before pushing) change we can make to the history is to update the previous commit.
This is useful just after we've made a commit, then realised we missed something, or made a mistake in the files or the commit message.

To modify the previous commit, use `git add` to stage the changes we missed out (if any), then create an `amend` commit:

``` sh
git commit --amend
```

An editor window will open populated with our previous commit message, giving us the chance to update it.

#### Exercise: Amend

Try this out and change the commit message, then have a look at the output of `git log --oneline --graph --all`, followed by `git reflog`.
Add a tag to the "missing" commit then rerun the above `git log` command.

### Reset the Branch

Another relatively simple change is to move the head of a branch.
This can be achieved with

``` sh
git reset <commit-sha>
```

The arguments supplied to `reset` change whether the workspace, the index or both are updated.

The command `git reset --soft` will update the index but leave the working directory unchanged.
This command is particularly useful for unstaging changes from the index.

In contrast, `git reset --hard` will change the `HEAD` and also change the files in the working directory to match.
We have to be especially careful with this command, since we can lose changes that haven't been commit anywhere.

#### Aside: The Stash

A useful command to quick store any unsaved changes is

``` sh
git stash
```

This takes the updates to our tracked files ans saves them into a local stash.
(It could be used as a safer equivalent to `git reset --hard HEAD`.)
We can then recover our changes with

``` sh
git stash pop
```

This action can even be performed on a different branch, providing us with a simple quick way of moving changes (say if we created a branch but forgot to switch to it).
Multiple sets of changes can be stored in the stash, they can be annotated with `--message`, and they can all be viewed with `git stash list`.
See the `git stash --help`  for extra features such as stashing untracked files, or moving stashed changes straight to a new branch.

### Rebase Instead of Merge

We have seen how we can use a merge to create a new commit with the changes from two branches:

``` none
    D--E feature
   /
  A--B--C main
```

From `main`, `git merge feature` would result in

``` none
    D----E feature
   /      \
  A--B--C--F main
```

where `F` has the changes from `B`, `C`, `D` and `E`.

An alternative strategy would be to **rebase** the `feature` branch to `main`.
In a rebase, the commits unique to the current branch are applied at the head of the specified branch.
Returning to the previous example before the merge:

``` none
    D--E feature
   /
  A--B--C main
```

If we are on the `feature` branch, then calling `git rebase main` would result in

``` none
          D'--E' feature
         /
  A--B--C main
```

Here the two original commits unique to `feature` (`D` and `E`) have been discarded, and two new commits with the same changes (`D'` and `E'`) have been applied starting at the head of `main`.
The result should be the same as the merge with a "simpler" history (assuming any conflicts are resolved in the same way).
However, we have rewritten the history to get here - if there are any references to the previous commits, they will appear to be in the history twice.

Merging or rebasing comes down to a matter of choice for the situation.
As with all rewrites to the history, it should be avoided when other people might have work on top of the commits which will be removed.

#### Aside: `rerere`

If you decide to make significant use of `rebase`, you may find yourself being asked to resolve the exact same conflicts multiple times.
In this case, enabling the tool `rerere`, or **reuse recorded resolution**, will save the user's fix of a conflict and reapply it each time it comes up.

### Interactive Rebase

TODO:

`git rev-list main..feature --oneline`
`git rebase -i HEAD~4`

### Summary

TODO:

### Exercise

TODO:
