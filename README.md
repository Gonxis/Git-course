# Git helper

### Git Terminology and CheatSheet

[Git Cheat Sheet](Git_Cheatsheet.pdf)
[Git Terminology](Git_Terminology.pdf)

### Git init

In order to use this command is that easy as positioning into the directory you like to initialize the repo: 
```
...Desktop$ mkdir new_repository_directory
...Desktop$ cd new_repository_directory
...Desktop/new_repository_directory$ git init
```
then you will have your git repository locally in your own machine 

### .Git Directory Contents

Here's a brief synopsis on each of the items in the .git directory:

* **config file** - where all project specific configuration settings are stored.
From the [Git Book](https://git-scm.com/book/en/v2/Customizing-Git-Git-Configuration):

> Git looks for configuration values in the configuration file in the Git directory (.git/config) of whatever repository you’re currently using. These values are specific to that single repository.

For example, let's say you set that the global configuration for Git uses your personal email address. If you want your work email to be used for a specific project rather than your personal email, that change would be added to this file.

* **description file** - this file is only used by the GitWeb program, so we can ignore it

* **hooks directory** - this is where we could place client-side or server-side scripts that we can use to hook into Git's different lifecycle events. Also can be used to hook into different parts or events of Git's workflow.
* **info directory** - contains the global excludes file
* **objects directory** - this directory will store all of the commits we make
* **refs directory** - this directory holds pointers to commits (basically the "branches" and "tags")

### Git clone

The command is `git clone` and then you pass the path to the Git repository that you want to clone. An optional value could be the new name of the cloning repository you want to set. In this example, we are cloning the `repo repo_to_clone` and set it a new name `cloned_repo`

```
git clone https://github.com/Gonxis/repo_to_clone cloned_repo
```

### Git status

The output of running `git status` in the new-git-project project:

```
$ git status
On branch master

No commits yet

nothing to commit (create/copy files and use "git add" to track)
```

The output tells us some things:

1. `On branch master` – this tells us that Git is on the `master` branch. You've got a description of a branch on your terms sheet so this is the "master" branch (which is the default branch). We'll be looking more at branches in lesson 5
2. `Your branch is up-to-date with 'origin/master'.` – Because git clone was used to copy this repository from another computer, this is telling us if our project is in sync with the one we copied from. We won't be dealing with the project on the other computer, so this line can be ignored.
3. `nothing to commit, working directory clean` – this is saying that there are no pending changes. 

### Git log

The command line `git log` will display *by default* the following:

* the SHA
* the author
* the date
* the message

It can display a lot more information than just this

#### Navigating The Log

When running the command line `git log`, will open in the terminal [Less](https://en.wikipedia.org/wiki/Less_(Unix)) editor. Here are some helpful keys:

* to scroll down, press
    * j or ↓ to move down one line at a time
    * d to move by half the page screen
    * f to move by a whole page screen
* to scroll up, press
    * k or ↑ to move _up_ one line at a time
    * u to move by half the page screen
    * b to move by a whole page screen
* press q to quit out of the log (returns to the regular command prompt)

#### Git log --oneline

```
git log --oneline
```

This command:

* lists one commit per line
* shows the first 7 characters of the commit's SHA
* shows the commit's message

#### Git log --stat

The `git log` command has a flag that can be used to display the files that have been changed in the commit, as well as the number of lines that have been added or deleted. The flag is `--stat` ("stat" is short for "statistics")

```
git log --stat
```

This command:

* displays the file(s) that have been modified
* displays the number of lines that have been added/removed
* displays a summary line with the total number of modified files and lines that have been added/removed

#### Git log -p

The `git log` command has a flag that can be used to display the actual changes made to a file. The flag is `--patch` which can be shortened to just `-p`

![Git log -p](img/git_log_-p.png)

Using the image above, let's do a quick recap of the `git log -p` output:

* 🔵 - the file that is being displayed
* 🔶 - the hash of the first version of the file and the hash of the second version of the file
    * not usually important, so it's safe to ignore
* ❤️ - the old version and current version of the file
* 🔍 - the lines where the file is added and how many lines there are
    * `-15,83` indicates that the old version (represented by the `-`) started at line 15 and that the file had 83 lines
    * `+15,85` indicates that the current version (represented by the `+`) starts at line 15 and that there are now 85 lines...these 85 lines are shown in the patch below
* ✏️ - the actual changes made in the commit
    * lines that are red and start with a minus (`-`) were in the original version of the file but have been removed by the commit
    * lines that are green and start with a plus (`+`) are new lines that have been added in the commit

### Git show

Running it like the example above will only display the most recent commit. Typically, a SHA is provided as a final argument:

```
$ git show fdf5493
```

The `git show` command will show *only one commit*. The output is exactly the same as the `git log -p` command. So by default, `git show` displays:

* the commit
* the author
* the date
* the commit message
* the patch information

However, `git show` can be combined with most of the other flags we've looked at:

* `--stat` - to show the how many files were changed and the number of lines that were added/removed
* `-p` or `--patch` - this the default, but if `--stat` is used, the patch won't display, so pass `-p` to add it again
* `-w` - to ignore changes to whitespace

### Helpful Links

#### Git init

* [Initializing a Repository in an Existing Directory](https://git-scm.com/book/en/v2/Git-Basics-Getting-a-Git-Repository#Initializing-a-Repository-in-an-Existing-Directory)
* [git init docs](https://git-scm.com/docs/git-init)
* [git init Tutorial](https://www.atlassian.com/git/tutorials/setting-up-a-repository)

#### Git clone

* [Cloning an Existing Repository](https://git-scm.com/book/en/v2/Git-Basics-Getting-a-Git-Repository#Cloning-an-Existing-Repository)
* [git clone docs](https://git-scm.com/docs/git-clone)
* [git clone Tutorial](https://www.atlassian.com/git/tutorials/setting-up-a-repository)

#### Git status

* [Checking the Status of Your Files](https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository#Checking-the-Status-of-Your-Files)
* [git status docs](https://git-scm.com/docs/git-status)
* [git status Tutorial](https://www.atlassian.com/git/tutorials/inspecting-a-repository/git-status)

#### Further Research

* [Version Control on Wikipedia](https://en.wikipedia.org/wiki/Version_control)
* [Centralized vs. DVCS from the Atlassian Blog](http://blogs.atlassian.com/2012/02/version-control-centralized-dvcs/)
* [Distributed version control on Wikipedia](https://en.wikipedia.org/wiki/Distributed_version_control)
* [Git Internals - Plumbing and Porcelain](https://git-scm.com/book/en/v2/Git-Internals-Plumbing-and-Porcelain)
* [Customizing Git - Git Hooks](https://git-scm.com/book/en/v2/Customizing-Git-Git-Hooks)
* [Generating patches with -p](https://git-scm.com/docs/git-diff#_generating_patches_with_p)