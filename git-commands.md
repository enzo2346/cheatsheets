## Summary

* [Initial Setup](#initial-setup)
* [Basics](#basics)
* [Branches](#branches)
* [Merge Rebase](#merge-rebase)
* [Tags](#tags)
* [Remote management](#remote-management)
* [Information Gathering](#information-gathering)
* [Fix Mistake](#fix-mistake)
* [Git Submodule](#git-submodule)
* [Basic Git Commands Cheatsheet](#basic-git-commands-cheatsheet)

## Initial Setup
### Setting up Git for the first time

```bash
git config --global init.defaultBranch main
git config --global user.name "Enzo Gallos"
git config --global user.email "gh@enzog.mozmail.com"
git config --global core.editor "code --wait"
git config --global grep.lineNumber true
git config --global alias.cm "commit -m"
git config --global alias.l 'log --graph --pretty=format:"%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset" --abbrev-commit'

```

To show your config list type:

```bash
git config --list
```

To edit it type:

```bash
git config --global -e
```

### Starting to work on a remote repository

#### I just want to clone this repository

If you simply want to clone this repository to run the code in your terminal.

```bash
git clone https://github.com/eptec-lab/Projet_CTF-GANG.git
```

#### My code is ready to be pushed to the repository

If you already have code ready to be sent to this repository, then execute this on your terminal.

```bash
cd existing-project
git init
git add --all
git commit -m "Initial Commit"
git remote add origin https://github.com/eptec-lab/Projet_CTF-GANG.git
git push -u origin HEAD:main
```

#### My code is already tracked by Git

If your code is already tracked by Git, then set this repository as your "origin" to push to.

```bash
cd existing-project
git remote set-url origin https://github.com/eptec-lab/Projet_CTF-GANG.git
git push -u origin --all
git push origin --tags
```

[Back to top](#summary)

## Basics

Git is a decentralized version management software. With this cheatsheet you will have a quick access to the most common git commands.

Create a git repository

```shell
git init
```
Clone an existing git repository

```shell
git clone <repository_url>
```

Stage changes for commit

```shell
git add <file1> <file2>   # Stage specific files
git add .                 # Stage all changes
```

Commit changes

```shell
git commit -m "Your commit message"
```

Push changes to remote repository

```shell
git push
```

Pull changes from remote repository

```shell
git pull
```

Show status of repository

```shell
git status
```

[Back to top](#summary)

## Branches

Git branches are a great way to organize your work. They allow you to work on different features in parallel and to merge them back into the main branch when they are ready.

Create a new branch

```shell
git branch <branch-name>
```

Create a new branch and switch to it

```shell
git checkout -b <branch-name>
```

Switch to a branch

```shell
git checkout <branch-name>
```

Delete a branch

```shell
git branch -d <branch-name>
```

Rename a branch

```shell
git branch -m <old-branch-name> <new-branch-name>
```

[Back to top](#summary)

## Merge Rebase

This cheatsheet contains commands to merge and rebase branches in your git repository.

Merge the main branch into the feature branch 

```shell
git checkout feature
git merge main
```

Or in one step:

```shell
git merge feature main
```
This creates a new “merge commit” in the feature branch that ties together the histories of both branches, giving you a branch structure that looks like this:

![Merge branch feature into main branch](https://wac-cdn.atlassian.com/dam/jcr:4639eeb8-e417-434a-a3f8-a972277fc66a/02%20Merging%20main%20into%20the%20feature%20branh.svg?cdnVersion=1373)

Rebase the feature branch onto main branch 

```shell
git checkout feature
git rebase main
```

This moves the entire feature branch to begin on the tip of the main branch, effectively incorporating all of the new commits in main. But, instead of using a merge commit, rebasing re-writes the project history by creating brand new commits for each commit in the original branch.

![Rebase branch feature onto main branch](https://wac-cdn.atlassian.com/dam/jcr:3bafddf5-fd55-4320-9310-3d28f4fca3af/03%20Rebasing%20the%20feature%20branch%20into%20main.svg?cdnVersion=1373)

You can also use pull to merge your branch with a remote branch:

1. Fetch the latest changes:

```shell
git fetch origin
```

2. Checkout your branch:

```shell
git checkout your_branch_name
```

3. Pull changes:

```shell
git pull origin remote_branch_name
```

4. Resolve conflicts

5. Commit merge changes

6. Push changes

[Back to top](#summary)

## Tags

This cheatsheet contains commands to create and manage tags in your git repository.

Create an annotated tag

```shell
git tag -a <tag-name> -m "Your tag message"
```

Without the `-m` option, git will open your default editor to enter the tag message.

Update a tag message

```shell
git tag -a <tag-name> -m "Your new tag message" -f
```

Delete a tag

```shell
git tag -d <tag-name>
```

Delete a tag on remote:

```shell
git push --delete origin <tag-name>
```

Push all tags to remote repository

```shell
git push --tags
```

Checkout to a tag

```shell
git checkout v1.4
```

List all tags

```shell
git tag
```

List all tags with content

```shell
git tag -n99
```

[Back to top](#summary)

## Remote Management

- List all remote repositories:

```shell
git remote -v
```
- Add a new remote repository:

```shell
git remote add <remote_name> <repository_url>
```

- Remove a remote repository:

```shell
git remote remove <remote_name>
```

- Rename a remote repository:

```shell
git remote rename <old_name> <new_name>
```

- Fetch changes from a remote repository:

```shell
git fetch <remote_name>
```

- Pull changes from a remote repository and merge them into the current branch:

```shell
git pull <remote_name> <branch_name>
```

- Push changes to a remote repository:

```shell
git push <remote_name> <branch_name>
```

- Push changes to a remote repository and set it as the default upstream branch:

```shell
git push -u <remote_name> <branch_name>
```

- Show information about a specific remote repository:

```shell
git remote show <remote_name>
```

- Update the URL of a remote repository:

```shell
git remote set-url <remote_name> <new_repository_url>
```

- Push all local branches to a remote repository:

```shell
git push --all <remote_name>
```

- Push all local branches and tags to a remote repository:

```shell
git push --all --tags <remote_name>
```

Remember to replace <remote_name> with the actual name of the remote repository and <branch_name> with the branch you want to interact with.

[Back to top](#summary)

## Information Gathering

This cheatsheet contains commands to gather information about your git repository.

Show current status of repository (staged and modified files): 

```shell
git status
```

Show changes in files: 

```shell
git diff
```

View a file in a prior commit: 

```shell
git show <commit>:<file>
```

Show log of commits: 

```shell
git log
```

Short tree representation of log: 

```shell
git log --all --graph --decorate --pretty=oneline --abbrev-commit
```

Tool integrated with git to visualize Git's internal mechanics:

```shell
gitk
```

Grep like to find pattern in files:

```shell
git grep <pattern>
```

[Back to top](#summary)

## Fix Mistake

This cheatsheet contains commands to fix mistakes in your git repository.

Change last commit message

```shell
git commit --amend
```

Delete uncommitted changes

```shell
git reset --hard
```

Undo the N most recent commit and keep changes

```shell
git reset HEAD~N
```

Undo most recent commit and get rid of changes

```shell
git reset HEAD~1 --hard
```

Remove untracked files from the working tree except the one specified in the pattern (including files in .gitignore)

```shell
git clean -xdfe <pattern>
```

Reset branch to remote state

```shell
git fetch origin
git reset --hard origin/[branch-name]
```

Rewrite commit history

```shell
git rebase -i HEAD~N
git push -f
```

[Back to top](#summary)

## Git Submodule

### Add Git submodule

Add a submodule to an existing repo:

```shell
git submodule add https://bitbucket.org/enzo/awesomelibrary
git add .gitmodules awesomelibrary/
git commit -m "added submodule"
git push
```

The commands above will create two new files in the repository `.gitmodules` and the `lib` directory. The contents of .gitmodules shows the new submodule mapping.

### Remove Git Submodule

Remove a submodule to an existing repo:

```shell
git submodule deinit .\awesomelibrary\
git rm .\awesomelibrary\
git commit -m "remove submodule"
git push
```

### Clone Git submodule

```shell
git clone https://github.com/enzo/MainProject
git submodule init
git submodule update
```

or

```shell
git clone --recurse-submodules https://github.com/enzo/MainProject
```

[Back to top](#summary)

## Basic Git Commands Cheatsheet

| Git task                          |                                                                                  Notes                                                                                 |                                       Git commands                                      |
|-----------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:---------------------------------------------------------------------------------------:|
| Tell Git who you are              |      Configure the author name and email address to be used with your commits.Note that Git strips some characters (for example trailing periods) from user.name.      | git config --global user.name "Sam Smith"git config --global user.email sam@example.com |
| Create a new local repository     |                                                                                                                                                                        |                                         git init                                        |
| Check out a repository            |                                                              Create a working copy of a local repository:                                                              |                              git clone /path/to/repository                              |
|                                   |                                                                        For a remote server, use:                                                                       |                       git clone username@host:/path/to/repository                       |
| Add files                         |                                                                Add one or more files to staging (index):                                                               |                                        git add *                                        |
| Commit                            |                                                     Commit changes to head (but not yet to the remote repository):                                                     |                              git commit -m "Commit message"                             |
|                                   |                                    Commit any files you've added with git add, and also commit any files you've changed since then:                                    |                                      git commit -a                                      |
| Push                              |                                                       Send changes to the main branch of your remote repository:                                                       |                                   git push origin main                                  |
| Status                            |                                                List the files you've changed and those you still need to add or commit:                                                |                                        git status                                       |
| Connect to a remote repository    |                               If you haven't connected your local repository to a remote server, add the server to be able to push to it:                              |                                  git remote add origin                                  |
|                                   |                                                           List all currently configured remote repositories:                                                           |                                      git remote -v                                      |
| Branches                          |                                                                  Create a new branch and switch to it:                                                                 |                                     git checkout -b                                     |
|                                   |                                                                   Switch from one branch to another:                                                                   |                                       git checkout                                      |
|                                   |                                         List all the branches in your repo, and also tell you what branch you're currently in:                                         |                                        git branch                                       |
|                                   |                                                                       Delete the feature branch:                                                                       |                                      git branch -d                                      |
|                                   |                                                    Push the branch to your remote repository, so others can use it:                                                    |                                     git push origin                                     |
|                                   |                                                              Push all branches to your remote repository:                                                              |                                  git push --all origin                                  |
|                                   |                                                               Delete a branch on your remote repository:                                                               |                                    git push origin :                                    |
| Update from the remote repository |                                                 Fetch and merge changes on the remote server to your working directory:                                                |                                         git pull                                        |
|                                   |                                                          To merge a different branch into your active branch:                                                          |                                        git merge                                        |
|                                   |                                 View all the merge conflicts:View the conflicts against the base file:Preview changes, before merging:                                 |                            git diff git diff --base git diff                            |
|                                   |                                               After you have manually resolved any conflicts, you mark the changed file:                                               |                                         git add                                         |
| Tags                              |                                                 You can use tagging to mark a significant changeset, such as a release:                                                |                                      git tag 1.0.0                                      |
|                                   |                                 CommitId is the leading characters of the changeset ID, up to 10, but must be unique. Get the ID using:                                |                                         git log                                         |
|                                   |                                                                   Push all tags to remote repository:                                                                  |                                  git push --tags origin                                 |
| Undo local changes                | If you mess up, you can replace the changes in your working tree with the last content in head:Changes already added to the index, as well as new files, will be kept. |                                     git checkout --                                     |
|                                   |             Instead, to drop all your local changes and commits, fetch the latest history from the server and point your local main branch at it, do this:             |                       git fetch origingit reset --hard origin/main                      |
| Search                            |                                                                 Search the working directory for foo():                                                                |                                     git grep "foo()"                                    |

[Back to top](#summary)