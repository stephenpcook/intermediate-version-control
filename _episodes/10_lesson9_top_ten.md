---
layout: page
title: Top 10 Topics Not Covered
order: 10
session: 2
length: 10
toc: true
adapted: false
---

## Top 10 (ish) Topics Not Covered

In the spirit of "you don't know what you don't know", here is a list of ten (ish) topics which were beyond the scope of the course.
Each topic is situational, but if any might apply to your work, links are provided for further reading.

### 1. Alternatives to git

There are many programs that can handle version control.
Two that are particularly popular and frequently compared to git are

- [Subversion (SVN)](https://subversion.apache.org/), and
- [Mercurial](https://www.mercurial-scm.org/).

### 2. Other forms of GitHub authentication

Two alternative to the personal access tokens are SSH keys and the git credential manager.

See [GitHub Authentication Document](https://docs.github.com/en/authentication) and [GCM](https://aka.ms/gcm).

### 3. Git hooks

Run local scripts during git steps, such as:

- pre-commit checks for syntax errors
- post-checkout report generation

See [Pro Git: Customizing Git - Git Hooks](https://git-scm.com/book/en/v2/Customizing-Git-Git-Hooks).

### 4. GitHub actions

Run workflows on remote servers after GitHub events, such as:

- Running a test suite before approving a pull request
- Generating and uploading documentation

See [GitHub Actions](https://github.com/features/actions).

### 5. Signing commits

Attach a signature to a local commit to verify yourself as the committer (otherwise anyone could use your name and e-mail address).

See [Pro Git: Git Tools - Signing Your Work](https://git-scm.com/book/en/v2/Git-Tools-Signing-Your-Work).

### 6. Git log grep and "pick-axe"

Git log can show only commits where changes match a search pattern, or be used to follow changes through line moves and file renames.

See [Pro Git: Git Tools - Searching](https://git-scm.com/book/en/v2/Git-Tools-Searching).

### 7. `git bisect`

Quickly find a specific change to behaviour by bisecting the history.
For example, find a change in 1024 commits in 10 steps, or in 2048 in 11 steps.

See [Git Docs: git-bisect](https://git-scm.com/docs/git-bisect).

### 8. Git Large File Storage

Git extension to upload large files and get a SHA, without tracking changes.

See [Git-LFS](https://git-lfs.com/)

### 9. Reduced clones (sparse-checkout, filtered checkout)

Options for reducing the download time of large repositories.
Can be

- Blobless: only downloads files as they're checked out (still aware of all history and file structure of history) -- `git clone --filter=blob:none <url>`
- Treeless: as blobless but also leaves out file tree for each commit; smaller download but some loss of functionality -- `git clone --filter=tree:0 <url>`
- Shallow clone: also leave out the history; local version of repository only has one commit! -- `git clone --depth=1`

See [GitHub Blog: Get up to speed with partial clone and shallow clone](https://github.blog/2020-12-21-get-up-to-speed-with-partial-clone-and-shallow-clone/)

### 10. Submodules

Include clones of other repositories in a subdirectory of your repository, with a reference to a commit.
(Submodules don't seem to be too popular, so other solutions might be preferable.)

See [Git Docs: git-submodule](https://git-scm.com/docs/git-submodule) and [Pro Git: Git Tools - Submodules](https://git-scm.com/book/en/v2/Git-Tools-Submodules).

### 11. `git blame`

Show the commit details next to each line in a file.
This is better seen on GitHub or in a IDE (such as VS Code) than with the `git blame` command.

See [GitHub Docs: Viewing the line-by-line revision history for a file](https://docs.github.com/en/repositories/working-with-files/using-files/viewing-a-file#viewing-the-line-by-line-revision-history-for-a-file).

### 12. Download a pull request

In some cases we might want to directly push to- or pull from- a pull request (say the author isn't responding).
We can see the full set of references on the remote with

``` sh
git ls-remote
```

See [GitHub Docs: Checking out pull requests locally](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/reviewing-changes-in-pull-requests/checking-out-pull-requests-locally).
