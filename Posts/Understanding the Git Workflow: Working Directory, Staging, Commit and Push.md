# The Ecosysytem
To understand the git workflow, we have to understand the ecosystem within which it exists.
- Git

This is a local version control system that tracks changes to files and code. It runs on every users local computer hence also known as an open source distributed version control system.
Whenever you create files or code, git is the software system that tracks these actions and ensures their integrity.

- Gitbash

Simply a command line interface. Like Git itself, it runs on your local computer and allows users to execute git commands.

- Github  

Github is the web based platform. Its an endpoint and host for all work done by users and various collaborative tools.
It is an interactive platform where creators and other users can view and even contribute to your work while giving you the benefit to control such interaction and contribution through access control tools.

For the git workflow to be complete, every aspect of this ecosystem has to work in harmony.

---

# The Workflow

The workflow follows an ordered sequence with various actions being perfomed in each sequence.
1. Working directory
2. Staging changes
3. Creating a commit
4. Pushing to a working repository

## Working directory

A github repository stores all files, folders and documentation related to a specific project. In git workflow, the repository is stored locally on your computer.
We established that git and gitbash run on your local computer, therefore for the software system, git, to manage and track changes, the repository has to be cloned to a path on your local computer.

Git can't manage data or code in the entire repository. The user has to define specific files on which to work on. This brings the concept of working directory. It simply means the specific path the code or file where you are currently using git to make and track changes.

### Establishing Your Working Directory

The crucial first step is to ascertain you are in the right directory. You use a set of command lines to do this.

> As opposed to windows `C:\Users` , in gitbash paths are mapped using unix style `/c/Users`

`pwd` shows you the current path you are in the directory. `ls` shows you the contents of your current directory. If you are in the wrong path you have a set of options to;

- navigate and access the right directory
- create a new directory or file
- list your current directory contents

1. **Navigate and access the right directory**
   | Command line | Function | Sample |
   | --- | --- | --- |
   | `pwd` | Show current directory | `pwd` |
   | `cd` | Change Directory | `cd Photos` |
   | `cd ..` | Up one level | `cd ../` |
   | `cd ../..` | Up two levels | `cd ../..` |
   | `cd ~` | Home Directory | `cd ~` |
   | `cd -` | Previous Directory | `cd -` |
   | `cd /` | Root | `cd /` |

2. **Creating new directory or file**
```
  mkdir folder_name                  # Create one directory
  mkdir folder1 folder2 folder3      # Create multiple
  mkdir -p path/to/nested/folders    # Create nested folders
  touch filename.txt                 # Create an empty file
  touch file1.txt file2.md file3.py  # Create multiple empty files
```

3. **Listing contents of your current directory**
  
   | Command line | Function |
   | --- | --- |
   | `ls` | All files |
   | `ls -l` | All files in detailed format |
   | `la -a` | All files, detailed including hidden files ` . ` |
   | `ls la` | Detailed plus hidden files |

The above processes show how to get to the right directory, you can then make changes and manage content using a variety of tools available.

## Staging in Git

You have done your changes in the working directory. What next? We learnt Git is a software and gitbash is the command line interface. Data, files and code in this format is unusable except by or through your local computer only. To collaborate, display and have these stored in a retrievable format; we need Github, the web interface.
Between your working directory and github, we go through 2 steps, first which is staging.

Staging in github is therefore self explanatory. Getting your changes prepared to be included in the next commit. This part of the sequence allows you to select what changes are commited.

1. **Check status in your working directory**

   ```git status```

   This command shows the status of changes in the directory. They could either be,
   - Untracked files/changes not staged for commit
   - changes to be commited (These are ready and prepared for commit)

2. **Stage unprepared files and folders**
   After ascertaining the unstaged files, use the command ```git add``` but in different versions to give you control of what to stage.

   | Command line | Function |
   | --- | --- |
   | `git add filename.txt` | Stage specific file |
   | `git add folder/` | Stage folder and all it's contents |
   | `git add .` | Stage all new and modified files in parent directory and all subdirectories |
   | `git add -A` or `git add --all`| Stage all new, modified and deleted files across the repository |
   | `git add -u` | Stage only modified and deleted files, excludes untracked or new files |
   | `git add -p` or `git add --patch` | Stage individual parts of a file|

4. Run `git status` again, at which point files should appear under *changes to be commited.*
   In case of any errors you have the following command prompts at your disposal.

   ```
   `git restore --staged filename.txt` to unstage a file
   `git restore --staged .` to unstage everything
   `git diff --staged` to see differences of staged files
   `git diff` to see unstaged files

##Commit

```
git commit -m "Clear description of what this commit does"
```

This command records the staged changes. *Note that at this point we are still in our local computer.* Unstaged changes therefore remain in our working directory.
 
> Another command `git commit -a` bypasses the `git -add` stage and stages all modified and deleted files in your working directory. See table below for variance between different commit command prompts.

| Feature | `git commit -a` | `git commit` | `git commit -am "msg"` |
| :--- | :--- | :--- | :--- |
| Stages modified files | Yes | No | Yes |
| Stages deleted files | Yes | No | Yes |
| Stages untracked (new) files | No | No | No |
| Opens text editor for message | Yes | Yes | Passes message inline |

A commit acts to move changes permanently from our staging area and makes them a permanent record. Git calls this a snapshot and is done in the `.git` folder. To see this folder you use the command we discussed earlier `ls -a` or `ls -la`.

Other actions that happen during this stage, git creates a commit object known as a Hash. It records the unique code changes, author name, timestamp, commit message, and the hash of the parent commit.

At this point, you can run `git status` again and if all is good you should see the message *“nothing to commit, working tree clean”.*

For any ammendments, you also have these at your disposal.

```
`git commit --ammend` Modifies most recent commit e.g add a file or edit commit m
`git commit --ammend -m "new message"` Cahnges message in last commit
`git commit --ammend --no -edit` Ammends last commit but keeps message
```
**Commit message**

Should be short and precise, preferably less than 50 characters. It summarily explains what was changed, why it was changes and any caution users should take. It should be done in present tense.

## Git Push

This is the last stage in the workflow. This uploads commits from your local repository to a web based platform, Github. This happens within the corresponding branch in your local and remote repository. At this point others can create edits, push and pull requests.

See table below for a summary of push commands.


   | Command line | Function |
   | --- | --- |
   | `git push` | Pushes current local branch to corresponding remote branch |
   | `git push origin main` | Specifies for git to push main branch in local repository to branch named origin in remote repository |
   | `git push -u origin main` | Pushes and reminds git to use this upstream relationship in subsequent push |
   | `git push origin feature -branch`| Pushes a feature branch |
   | `git push --all` | Pushes all local branches |
   | `git push --tags` | Pushes Tags as well |

**Summary**

This workflow can be summarised as a local to remote workflow.

> Working Directory  →  Staging Area  →  Commit  →  Remote Repository
    
> ---
