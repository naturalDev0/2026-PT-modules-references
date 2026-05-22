# Recap 18 May 2026 - Git and Github

## Git

### Commands

#### add

```bash
# select files to create save point
# move the files into staging
git add file_name.txt file_name_2.txt ...

# add every changes from all working directories and subdirectories
git add .
git add * # OR this
```

##### Difference between `git add .` and `git add *`

| **Feature / Behavior**            	| **`git add .`**                             	| **`git add *`**                             	|
|-----------------------------------	|---------------------------------------------	|---------------------------------------------	|
| Who interprets the command?       	| Git itself                                  	| Your terminal shell (Bash, Zsh, etc.)       	|
| Hidden files (.env, .gitignore    	| Staged (Includes everything)                	| Ignored (Shell wildcards skip dotfiles)     	|
| Deleted files (Modern Git)        	| Staged                                      	| Staged                                      	|
| Files in parent/outer directories 	| Ignored (Only looks down from current path) 	| Ignored (Only looks down from current path) 	|
| Subdirectory contents             	| Staged (Recurses deeply)                    	| Staged (Recurses deeply)                    	|
| Accidental credential leaks       	| High risk (Easily stages hidden .env files) 	| Low risk (Skips root hidden files)          	|****

##### Key Takeaway between `git add .` and `git add *`
* Use `git add .` when you want a blanket save of everything in your current directory, <ins>including configuration files</ins>.
* Use `git add *` when you want to stage all visible files while <ins>intentionally leaving your hidden configuration files alone</ins>.

#### commit

```bash
# create save point
# compile all the files together into your local repository
git commit -m "write your message here"

# e.g. removed the bug_report as no longer in use.
git commit -m "remove bug report"

# output
[task_a 251efd8] remove bug report
 1 file changed, 0 insertions(+), 0 deletions(-)
 delete mode 100644 bug_report_1.txt

# industry practice
git commit -m "title of the commit" -m "body message of the commit"
```

#### push

```bash
# upload your "save points" aka commits to remote repository
git push remote_name branch_name

# e.g. upload new `hotfix1` branch to remote `origin`
git push --set-upstream origin hotfix1

# output
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 22 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 308 bytes | 308.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
remote: 
remote: Create a pull request for 'hotfix1' on GitHub by visiting:
remote:      https://github.com/naturalDev0/firsts_demo_project/pull/new/hotfix1
remote: 
To https://github.com/naturalDev0/firsts_demo_project.git
 * [new branch]      hotfix1 -> hotfix1
branch 'hotfix1' set up to track 'origin/hotfix1'.


# OR when your branch is tracked (meaning, upstream)
# How do we know? Refer to `git branch` section of this document.
git push
```

#### branch

```bash
# (1) view existing branches
git branch

# output (1)
  feature1
  feature2
* hotfix1
  main


# (2) OR view latest commit details in branch
git branch --verbose
git branch -v # shorthand

# output (2)
  feature1 37e0192 fourth file
  feature2 df23d70 new files added.
* hotfix1  23ed3fc bug is fixed. report is generated.
  main     23ed3fc [ahead 2] bug is fixed. report is generated.


# (3) OR view with upstream details
git branch -vv

# output (3)
  feature1 37e0192 fourth file
  feature2 df23d70 [origin/feature2] new files added.
* hotfix1  23ed3fc bug is fixed. report is generated.
  main     23ed3fc [origin/main: ahead 2] bug is fixed. report is generated.


# (4) Show all branches including remote branches
git branch -a

# output (4)
  feature1
  feature2
* hotfix1
  main
  remotes/origin/feature2 # exist on remote repo
  remotes/origin/main # exist on remote repo


# (5) Delete branch
git branch -d branch_name
# e.g. delete feature1 branch
git branch -d feature1

# output (5)
Deleted branch feature1 (was 37e0192).
```

#### remote

```bash
# (1) view available remote repositories
git remote

# output (1)
origin

# (2) view available remote repos in detailed
git remote --verbose
git remote -v

# output (2)
origin  https://github.com/naturalDev0/firsts_demo_project.git (fetch)
origin  https://github.com/naturalDev0/firsts_demo_project.git (push)
```

#### status

```bash
# view current working branch has any movements
# e.g. new/modified/deleted files
# merge conflicts, etc.
git status


# outputs

# (1) when everything is clear
On branch task_a
nothing to commit, working tree clean

# (2) when a file is deleted
On branch task_a
Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        deleted:    readpeople.txt

no changes added to commit (use "git add" and/or "git commit -a")

# (3) when a new file is added
On branch task_a
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        tonight.md

nothing added to commit but untracked files present (use "git add" to track)

# (4) when a file is modified
On branch task_a
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   readyou.md

no changes added to commit (use "git add" and/or "git commit -a")
```

#### log

```bash
# view the logs details
# i.e., commit unique key (SHA), author's name and email
# commit timestamp, etc.
git log

# output
commit 9b58438bc57796f3e2da0019365db34b742b4168
Author: tommy <tommy@email.com>
Date:   Mon May 18 22:22:32 2026 +0800

    second file.

commit 9eef8f6457fc026fa4347dd6d2ab2efdeebeac2a
Author: tommy <tommy@email.com>
Date:   Mon May 18 21:58:40 2026 +0800

    this is my first commit
```

#### checkout

```bash
# switch to another branch
git checkout branch_name

# e.g. switch to main branch
git checkout main

# output
Switched to branch 'main'
Your branch is ahead of 'origin/main' by 2 commits.
  (use "git push" to publish your local commits)


# OR create a new branch and switch to it
git checkout -b branch_na

# e.g. create branch name, task_a, and switch to it.
git checkout -b task_a

# output
Switched to a new branch 'task_a'
```

#### merge

```bash
# merge changes from another branch(es)
# !NOTE: Always check out the target branch first
# before merging the source into it.
# e.g. merging task_a into main

git checkout main # OR skip this if you're inside

git merge task_a # merge task_a into main

# output
Updating 23ed3fc..db88e7d
Fast-forward
 bug_report_1.txt | 0
 readyou.md       | 1 +
 2 files changed, 1 insertion(+)
 delete mode 100644 bug_report_1.txt
```

#### config

```bash
# list the local git configurations
git config --list

# set commit credentials in configurations
# when you type `git commit`, git logs down the author
# details using the following parameters set.
git config user.name "your name"
git config user.email "your email address"
```

## Github

### Cloning Github repository from VS Code

1. Go to existing github repository

2. Select `<> Code` button --> Select `HTTPS` --> Copy the weblink starts with `https:...`

3. Open your VS Code (make sure is a fresh new window)

4. Select `Source Control` button (located on the left pane)

5. Select `Clone Repository` > Paste weblink on the prompt > Press `Enter` to confirm

6. Depending on which OS you're on:
   
   1. MacOS    - fill in sign-in details on git credentials helper
      when prompted.
   2. Windows  - don't require.

7. Select the desired folder location to download the repository.

8. Done! You've successfully downloaded the repository on your local computer.
