## Commands
A command is a directive to a computer program to perform a specific task. We are going to learn how to use them.

# Directories
mkdir: It is the directory name, used to create a new directory. 
rmdir: It is used to remove a directory.

# Navigate
cd: (where "cd" stands for "change directory") It is used to change this current working directory.

# Compare
cmp: It is used to track the difference between the changes made on a file. It takes two inputs and reflects the differences between them.

# Find files
find .-name: Allows us to view files as they existed in a previous state.

# Create and edit files
nano: Used to create or edit, just type nano followed by the name of the file.

#State of the computer
lscpu: Lets you see the state of the computer and limit the output it produces to only online or offline CPUs.

## Git Commands
Working with Git on the command line can be daunting. To help with that, I’ve put together a list of common Git commands, what each one means, and how to use them.

# Initial Configuration
With Git, there are many configurations and settings possible. git config is how to assign these settings.
$ git config --global user.email "your email": set what email commits will be from on a local computer.
example: $ git config --global user.email "2009130@upy.edu.mx"

$ git config --global user.name "your name": set what name commits will be from on a local computer.
example: $ git config --global user.name "anasosa"

# Start or clone
Use this commands when you want to start or create a repository.
$ git init: This command turns a directory into an empty Git repository.After running git init, adding and committing files/directories is possible.
example: 
$ git init
Initialized empty Git repository in /Users/computer-name/Documents/website/.git/

$ git clone <remote_URL>: use git clone to copy and download the repository to a computer.
example: 
$ git clone git@account_name.git.beanstalkapp.com:/acccount_name/repository_name.git
Cloning into 'repository_name'...
remote: Counting objects: 5, done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 5 (delta 0), reused 0 (delta 0)
Receiving objects: 100% (5/5), 3.08 KiB | 0 bytes/s, done.
Checking connectivity... done.

# Basic Workflow
$ git status: This command returns the current state of the repository. If a file is in the staging area, but not committed, it shows with git status. Or, if there are no changes it’ll return nothing to commit, working directory clean.
example: 
 #Message when files have not been staged (git add)
$ git status
On branch SecretTesting
Untracked files:
  (use "git add <file>..." to include in what will be committed)

  	homepage/index.html

 #Message when files have been not been committed (git commit)
$ git status
On branch SecretTesting
Your branch is up-to-date with 'origin/SecretTesting'.
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        new file:   homepage/index.html

 #Message when all files have been staged and committed 
$ git status
On branch SecretTesting
nothing to commit, working directory clean

$ git add <file or directory name>: Adds files in the to the staging area for Git. There are a few different ways to use git add, by adding entire directories, specific files, or all unstaged files.
example:
 #To add all files not staged:
$ git add .

 #To stage a specific file:
$ git add index.html

 #To stage an entire directory:
$ git add css

$ git commit -m "Commit message": Record the changes made to the files to a local repository. For easy reference, each commit has a unique ID.
example: 
$ git commit -m "My first commit message"
[SecretTesting 0254c3d] My first commit message
1 file changed, 0 insertions(+), 0 deletions(-)
create mode 100644 homepage/index.html

$ git rm --cached <file name>: To remove a file from the working index (cached).
example:
$ git rm --cached css/style.css
rm 'css/style.css'

$ git rm -f <file name>: To delete a file (force).
example: 
$ git rm -f css/style.css
rm 'css/style.css'

$ git rm -r --cached <directory name>: To remove an entire directory from the working index (cached).
example:
$ git rm -r --cached css/
rm 'css/style.css'
rm 'css/style.min.css'

$ git rm -r -f <file name>: To delete an entire directory (force).
example: 
$ git rm -r -f css/
rm 'css/style.css'
rm 'css/style.min.css'

$ git stash -u: Store current work with untracked files.
example:
$ git stash -u
Saved working directory and index state WIP on SecretTesting: 4c0f37c Adding new file to branch
HEAD is now at 4c0f37c Adding new file to branch

$ git stash pop: Bring stashed work back to the working directory.
example:
$ git stash pop
On branch SecretTesting
Your branch and 'origin/SecretTesting' have diverged,
and have 1 and 1 different commit each, respectively.
  (use "git pull" to merge the remote branch into yours)
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   index.html

no changes added to commit (use "git add" and/or "git commit -a")
Dropped refs/stash@{0} (3561897724c1f448ae001edf3ef57415778755ec)

$ git log: Show entire git log
example:
$ git log
commit 4c0f37c711623d20fc60b9cbcf393d515945952f
Author: Brian Kerr <my@emailaddress.com>
Date:   Tue Oct 25 17:46:11 2016 -0500

    Updating the wording of the homepage footer 
    
commit 0254c3da3add4ebe9d7e1f2e76f015a209e1ef67
Author: Ashley Harpp <my@emailaddress.com>
Date:   Wed Oct 19 16:27:27 2016 -0500

    My first commit message

$ git log --<after/before/since/until>=<date>:  Show git log with date pameters.
example: 
$ git log --before="Oct 20"
commit 0254c3da3add4ebe9d7e1f2e76f015a209e1ef67
Author: Ashley Harpp <my@emailaddress.com>
Date:   Wed Oct 19 16:27:27 2016 -0500

    My first commit message

$ git log --<author>="Author Name": Show git log based on commit author.
example:
$ git log --author="Brian Kerr"
commit 4c0f37c711623d20fc60b9cbcf393d515945952f
Author: Brian Kerr <my@emailaddress.com>
Date:   Tue Oct 25 17:46:11 2016 -0500

    Updating the wording of the homepage footer

# Remote 
$ git remote <command> <remote_name> <remote_URL>: Add remote repository.
example:
$ git remote add origin git@account_name.git.beanstalkapp.com:/acccount_name/repository_name.git

$ git remote -v: List named remote repositories.
example:
$ git remote -v
origin git@account_name.git.beanstalkapp.com:/acccount_name/repository_name.git (fetch)
origin git@account_name.git.beanstalkapp.com:/acccount_name/repository_name.git (push)

$ git push <remote_URL/remote_name> <branch>: Push a specific branch to a remote with named remote.
example:
$ git push origin staging
Counting objects: 5, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (3/3), done.
Writing objects: 100% (5/5), 734 bytes | 0 bytes/s, done.
Total 5 (delta 2), reused 0 (delta 0)
To git@account_name.git.beanstalkapp.com:/acccount_name/repository_name.git
   ad189cb..0254c3d  SecretTesting -> SecretTesting

$ git push —all: Push all local branches to remote repository.
example:
$ git push --all
Counting objects: 4, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (4/4), done.
Writing objects: 100% (4/4), 373 bytes | 0 bytes/s, done.
Total 4 (delta 2), reused 0 (delta 0)
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
To git@account_name.git.beanstalkapp.com:/acccount_name/repository_name.git
   0d56917..948ac97  master -> master
   ad189cb..0254c3d  SecretTesting -> SecretTesting

$ git pull <branch_name> <remote_URL/remote_name>: To get the latest version of a repository run git pull. This pulls the changes from the remote repository to the local computer.
example:
$ git pull origin staging
From account_name.git.beanstalkapp.com:/account_name/repository_name
 * branch            staging    -> FETCH_HEAD
 * [new branch]      staging    -> origin/staging
Already up-to-date.
$ git pull git@account_name.git.beanstalkapp.com:/acccount_name/repository_name.git staging
From account_name.git.beanstalkapp.com:/account_name/repository_name
 * branch            staging    -> FETCH_HEAD
 * [new branch]      staging    -> origin/staging
Already up-to-date.

# Branches
$ git branch <branch_name>: Create a new branch.
example:
$ git branch new_feature

$ git branch -a: List all remote or local branches.
example:
$ git branch -a
* SecretTesting
  new_feature
  remotes/origin/stable
  remotes/origin/staging
  remotes/origin/master -> origin/SecretTesting

$ git branch -d <branch_name>: Delete a branch.
example:
$ git branch -d new_feature
Deleted branch new_feature (was 0254c3d).

$ git checkout <branch_name>: Checkout an existing branch.
example: $ git checkout new_feature
Switched to branch 'new_feature'

$ git checkout -b <new_branch>: Checkout and create a new branch with that name.
example:
$ git checkout -b staging
Switched to a new branch 'staging'

$ git merge <branch_name>: Merge changes into current branch.
example:
$ git merge new_feature
Updating 0254c3d..4c0f37c
Fast-forward
 homepage/index.html | 297 ++++++++++++++++++++++++++++++++++++++++++++++++++++++++
 1 file changed, 297 insertions(+)
 create mode 100644 homepage/index.html

## Gitflow

# Initialization
To initialize a new repo with the basic branch structure, use: git flow init [-d]

# Creating
To list/start/finish feature branches, use:

  git flow feature
  git flow feature start <name> [<base>]
  git flow feature finish <name>

To push/pull a feature branch to the remote repository, use:

  git flow feature publish <name>
    git flow feature pull <remote> <name>

To list/start/finish release branches, use:

  git flow release
  git flow release start <release> [<base>]
  git flow release finish <release>

To list/start/finish hotfix branches, use:

  git flow hotfix
  git flow hotfix start <release> [<base>]
  git flow hotfix finish <release>

To list/start support branches, use:

  git flow support
  git flow support start <release> <base>
