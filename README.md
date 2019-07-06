# git_basics

This article covers the basic operations of git and help beginners start their version control of projects.

## Check version
After installation of git on your machine, you can check the version of your git in the git bash
```
git --version
```

## Config git, set up the user name and email in git
```
git config --global user.name <your name>
git config --global user.email <your email>
```
You can check the config values by
```
git config --list
```

## Need help?
```
git help config
git config --help
```

## Get started (Two common scenerios)
- Initialize a repo from existing code
Simply run the init command within the directory from the terminal
```
git init
```
Then we can create a remote directory in any remote git server, such as github, gitlab, bitbucket and so. In order to link the local directory with the remote directory, we need to add the remote repository to the remote
```
git remote add origin <git repo url>
```
- Cloning a remote repo
We can use the following command to clone a remote repo to our local working directory
 ```
 git clone <url> <where to clone>
 ```


## View information about the remote repository
```
git remote -v
```
List all branches
```
git branch -a
```