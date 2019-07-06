# **git_basics**

This article covers the basic operations of git and help beginners start their version control of projects.

## Check version
After installation of git on your machine, you can check the version of your git in the terminal
```
$ git --version
```

## Config git

Confiure user information for all local repositories
```
$ git config --global user.name [name]
Sets the name attached to your commit transactions
```
```
$ git config --global user.email [email]
Sets the email attached to your commit transactions
```
```
$ git config --list
Lists all the configuration information
```


## Get started

There are two ways to use git to start version control:

- Initialize a repository from existing code

    1. Simply run the `init` command within the directory from the terminal
```
$ git init [project-name]
Creates a new local repository with the specified name
```

    2. Create a remote repository in any remote git server, such as github, gitlab, bitbucket and so on. In order to link the local repository with the remote repository, we need to add the remote repository to the remote
```
$ git remote add origin [url]
Adds a new remote named 'origin' with the specific url
```

- Clone a remote repository

    1. Clone a remote repository to our local working directory
    ```
    $ git clone [url] [where to clone]
    Downloads a project and its entire version history
    ```

    2. View information about the remote repository
    ```
    $ git remote -v
    ```
    ```
    $ git branch -a
    Lists all branches
    ```

## Simple git workflow

1. Make changes in the local working directory
2. Before commit
```
$ git status
Lists all new or modified files to be committed
```
```
$ git diff
Shows file differences not yet staged
```
```
$ touch .gitignore
Creates a .gitignore file that excludes files and paths 
```
    In `gitignore`, simply put the names of the files and folders you don't want to track. For example,
```
.DS_Store
build/
venv
.*pyc
```

3. Add files to staging area
```
$ git add -A
Snapshots the file in preparation for versioning
```
...`-A` means staging all modified files. You can also specify the file name to add the specific file.

```
$ git status
```

4. Remove files from staging area
```
$ git reset [filename]
Unstages the file, but preserve its contents
```
...If `[filename]` is omitted, git will unstage all files.

```
$ git status
```

5. Commit the changes
```
$ git commit -m [descriptive message]
Records file snapshots permanently in version history
```

Commit message needs to be detailed and concise. You can also use `git log` to show the details of the commit.

6. Push changes
```
$ git pull origin master
Fetches new commits from the remote master branch and merge with the current working branch
```
```
$ git push origin master
Pushes the new commits from the current working branch to the remote master branch
```

`origin` is the name/alias of the `remote` repository. `master` is the name of the `remote branch`. *Always `pull` first before you `push` changes to the remote* because your collaborators may have made changes to the remote repository and you want to make sure your local repository is up-to-date. Otherwise, you may produce conflicts when you `push`.


A quick recap of how git works:
```
$ git diff
$ git status
$ git add -A
$ git commit -m [commit message]
$ git pull origin master
$ git push origin master
```

## Common git workflow in a project
1. Create a branch for desired feature

In the local directory, 
```
$ git branch demo
Creates a new branch called 'demo'
```
You can view all local branches by `git branch`. You can also view all branches by `git branch -a`. 

2. Switch to the `demo` branch
```
$ git checkout demo
Switches to the 'demo' branch and uptes the working directory
```

3. Make changes in the `demo` branch and `commit` changes to the local `demo` branch

4. After commit, push branch to `remote`
```
$ git push -u origin demo
```
Now we create a new branch in the remote repository. Our collaborators can perform unittesting or code review using the `remote demo` branch before we `merge` branches. `-u` sets up the `-upstream` for git so that in future, when we `push` or `pull`, we don't need to specify the name of the remote repo and branch. Simply use `git pull` and `git push`.

5. Merge a branch

We make sure our changes work well and need to merge our working branch with the master branch. First, switch to the local master branch
```
$ git checkout master
```
Make sure the master branch is up-to-date
```
$ git pull origin master
```
Check if the branch has been merged or not
```
$ git branch --merged
```
If not, merge the branch with the current branch (local master)
```
$ git merge demo
Combines the specified branch's history into the current branch
```
At the end, push our local master to the remote repository
```
$ git push origin master
```

6. Delete a branch

Delete the local `demo` branch
```
$ git branch -d demo
Deletes the specified branch ('demo')
```
```
$ git push origin --delete demo
Delete the remote `demo` branch
```
Verify the branches have been successfully deleted
```
$ git branch -a
```

## Other useful git commands

### Save fragments

`stash` saves the current work. The repository will go back to the state without all uncommitted changes (cleaner state). Then you can make some quick changes or try some new ideas. Finally you can restore the uncommitted changes. 
```
$ git stash
Temporarily stores all modified tracked files
```
do/fix something quickly
```
$ git stash pop
Restores the most recently stashed files
```
```
$ git stash list
Lists all stashed changesets
```
```
$ git stash drop
Discards the most recently stashed changeset
```

### Undo commit
```
$ git reset [commit]
Undoes all commits after [commit], preserving changes locally
```
```
$ git reset --hard [commit]
Discards all history and changes back to the specified commit
```

### Review history

```
$ git log
Lists version history for the current branch
```
```
$ git diff [first-branch]...[second-branch]
Shows content diffences between two branches
```
```
$ git show [commit]
Outputs metadata and content changes of the specified commit
```

### Refactor filenames
```
$ git rm [filename]
Deletes the file from the working directory and stages the deletion
```
```
$ git mv [file-original] [file-renamed]
Changes the file name and prepares it for commit
```

## Need help?
```
$ git help [command]   
$ git [command] --help
``` 
