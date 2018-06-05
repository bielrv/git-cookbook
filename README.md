# git-cookbook [![Build Status](https://travis-ci.org/bielrv/git-cookbook.png?branch=master)](https://travis-ci.org/bielrv/git-cookbook)

This repository contains instructions and information on how to use github.

>Git is the open source distributed version control system that facilitates GitHub activities on your laptop or
desktop. This cheat sheet summarizes commonly used Git command line instructions for quick reference.

1. [Git schema](#1)
1. [Git files](#2)
1. [Start a new Git repository for an existing code base](#3)
1. [Removing folder from remote repository](#4)
1. [Git cheat sheet](#5)
   * [Create repositories](#5.1)
   * [Make changes](#5.2)
   * [Group Changes](#5.3)
   * [Review history](#5.4)
   * [Synchronize changes](#5.5)
1. [Useful options](#6)
1. [Git Setup](#7)
1. [Git Configuration](#8)
***

# <a id="1"></a> 1. Git schema 

![](git-schema.png?raw=true)

***

# <a id="2"></a> 2. Git files

- [x] .git -> The Git repository is stored in the same directory as the project itself, in a subdirectory called .git.
- [x] readme.md -> Generates the html summary you see at the bottom of projects
- [x] .gitignore -> Specifies intentionally untracked files to ignore 
- [x] license -> Allows an open source license in the repository to make it easier for other people to contribute

# <a id="3"></a> 3. Start a new Git repository for an existing code base
```shell
cd /path/to/my/codebase
git initk
git add .
git commit
```
Creates an empty .git file in current repository or reinitialize an existing one.
```shell
git init
```
Add all existing files to the index.
```shell
git add .
```
Record the pristine state as the first commit in the history.
```shell
git commit -m "First commit"
```

Add remote repository to local repository.
```shell
git remote add origin remote repository URL
# Sets the new remote
git remote -v
# Verifies the new remote URL
```

***

# <a id="4"></a> 4. Removing folder from remote repository
*This will not remove the folder from your local repository*
```shell
git rm -r --cached FolderName
git commit -m "Removed folder from repository"
git push origin master
```
**Use** `.gitignore` **to ignore that folder in future commits**

***

# <a id="5"></a> 5. Git cheat sheet 

## Create repositories </a>
*Start a new repository or obtain one from an existing URL*\
`git init [project-name]` creates a **new local repository** with the specified name\
`git clone [url]` downloads an **existing project** and its entire version history

***

##  <a id="5.1"></a>  Make changes 
*Review edits and craf a commit transaction*\
`git status` lists all new or modified files to be commited\
`git diff` shows changes between commits\
`git add [file]` snapshots the file in preparation for versioning\
`git diff --staged` shows file differences between staging and the last file version\
`git reset [file]` unstages the file, but preserve its contents\
`git commit -m "[descriptive message]"` records file snapshots permanently in version history

***

## <a id="5.2"></a> Group Changes 
*Name a series of commits and combine completed efforts*\
`git branch` lists all local branches in the current repository\
`git branch [branch-name]` creates a new branch\
`git checkout [branch-name]` switches to the specified branch and updates the working directory\
`git merge [branch]` combines the specified branch’s history into the current branch\
`git branch -d [branch-name]` deletes the specified branch

***

## <a id="5.3"></a> Refactor filenames 
*Relocate and remove versioned files*\
`git rm [file]` deletes the file from the working directory and stages the deletion\
`git rm --cached [file]` removes the file from version control but preserves the file locally\
`git mv [file-original] [file-renamed]` changes the file name and prepares it for commit

***

## <a id="5.4"></a> Review history
*Browse and inspect the evolution of project files*\
`git log` lists version history for the current branch\
`git log --follow [file]` lists version history for a file, including renames\
`git diff [first-branch]...[second-branch]` shows content differences between two branches\
` git show [commit]` outputs metadata and content changes of the specified commit

***

## <a id="5.5"></a> Synchronize changes
*Register a repository bookmark and exchange version history*\
`git fetch [bookmark]` downloads all history from the repository bookmark\
`git merge [bookmark]/[branch]` combines bookmark’s branch into current local branch\ 
`git push [alias] [branch]` uploads all local branch commits to GitHub\
`git pull` downloads bookmark history and incorporates changes

***

`git-clean` removes untracked files from the working tree\
`git-gc` cleans up unnecessary files and optimize the local repository\
`git-gui` is a portable graphical interface to Git\
`git-merge` joins two or more development histories together\
`git-rm` removes files from the working tree and from the index\
`git-worktree` manages multiple working trees

***

# <a id="6"></a> 6. Usefull options

Option | Description
------------ | -------------
**--version**|Prints the Git suite version that the git program came from.
**--help**|Prints the synopsis and a list of the most commonly used commands.
**--force**|Useful when repo refuses to update a remote repo. Usually due to ref.
**--hard**|Clears staging area and rewrites working tree from a commit when used with reset.
**--verbose**|Be a little more verbose.
**--global**|Applies to all repositories.
**--stats**|Show all commit logs with indications when used with log.
**--follow**|Shows a file changes even across renames when used with log.

# <a id="7"></a> 7. Git Setup
`git config --global user.name "[firstname lastname]"` sets a name that is identifiable for credit when review version history
`git config --global user.email "[valid.email]"` sets an email address that will be associated with each history marker
`git config --global color.ui auto` sets automatic command line coloring for GIt for easy reviewing

[Useful git cheat sheet PDF](https://services.github.com/on-demand/downloads/github-git-cheat-sheet.pdf)

# <a id="7"></a> 7. Git Configuration
`--replace-all` Default behavior is to replace at most one line. This replaces all lines matching the key (and optionally the value_regex).  
`--add`  Adds a new line to the option without altering any existing values. This is the same as providing ^$ as the value_regex in `--replace-all`
