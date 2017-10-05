---
author: GrantMeStrength
---

**Windows Open Publishing Guide has been deprecated**

The content here has not been updated and may no longer be accurate.

**Please refer to the Windows Authoring Guide for up-to-date authoring information: [https://aka.ms/WindowsAuthoring](https://aka.ms/WindowsAuthoring)**


# Git cheatsheet

This page provides some help when you are using the command line version of git. Feel free to augment, correct, and annotate.

## Creating repos, adding files, committing

Git stores files (for example, plain text, markdown files, source code) in a database called a *repo*. Repos can be created and used locally (i.e. on your PC and nowhere else), or created on a server (such as GitHub) and copied (a.k.a. cloned) to create a local version. You can then work in the local version, and send changes to the server version as required. A remote repo can be shared by multiple users at once, and git provides tools for managing any conflicting changes.

| Task                                                                                                                        | Command line                                | Notes                                                                                                                                                                                                                                                                                                                                                                             |
|-----------------------------------------------------------------------------------------------------------------------------|---------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Clone an existing remote repo to your PC                                                                                   | `git clone <repo name>`                       | For example: `git clone https://github.com/Microsoft/windows-apps` will copy the remote repo to the current directory on your local PC.                                                                                                                                                                                                                                             |
| Create a new repo locally on your PC                                                                                       | `git init`                                    | Useful for testing git on your local PC. Not to be confused with branching.                                                                                                                                                                                                                                                                                                       |
| Add any files in the current local directory to the list ready to be added to the repo; these files are said to be tracked | `git add -A`                                  | The files are not yet added to the repo; they are added to the list of files that will be added when you do a commit.                                                                                                                                                                                                                                                             |
| Add a specific file to the list of tracked files, ready to be added to the repo                                           | `git add <file name>`                         | If you only need to add a specific file, or file pattern such as *.gif, use this command. Alternate usage: mark a file as merged when resolving merge conflicts.                                                                                                                                                                                                                  |
| List changes to any tracked files                                                                                          | `git diff`                                | After you commit the changes, diff will have nothing to display. Diff only displays changes you have made before committing them.                                                                                                                                                                                                                                                  |
| Remove a file from the file list                                                                                           | `git rm –cached <file name>`                  | Added a file by mistake? Here’s how you remove it. The file will not be deleted, only removed from the list of tracked files.                                                                                                                                                                                                                                                     |
| Get current status                                                                                                          | `git status`                                  | Display the files to be committed, the current branch you’re on, etc.                                                                                                                                                                                                                                                                                                              |
| Add an existing file to the current git repo                                                                               | `git commit –a –m “Your commit message here”` | Git will take the files you have added using the `add` command, and add them to the local repo. The message can be useful when looking through logs, so add useful information to it, such as “Corrected bug #123212” or “New Introducing Cooking with Windows topic.” Remember: The file you added is still only added to the local repo. Nothing has changed on any remote git repo.                                                                                                                                                                                                                                                     |
| Undo the commit                                                                                                          | `git commit -amend`                                  | If you are using a local repo, this does what you expect. If you are using a remote repo, you can undo the commit as long as you haven’t pushed the changes.                                                                                                                                                                                                            |                                                                                                  | 


## Branches

Branches are a good way to make changes that you are not sure you want to keep. Branches are a copy of the existing master branch (or another branch if you have created one). You can work in the branch, and then either delete it, or merge the changes back into the original. Branches let you keep multiple versions of your files on your local system at the same time, and switch between them as required.

| Task |	Command line	| Notes |
|------|----------------|-------|
| Create a new branch	| `git branch <name of branch>`	| You must have at least one commit performed in the existing repo before creating a new branch. Note: this command will not switch to the current branch, it will only create it. Use `git checkout <branch>` to switch branches. |
| Switch to a previously created branch	| `git checkout <name of branch>`	| Use `git checkout master` to return to the initial branch. |
| Merge a branch |	`git merge <name of branch>`	| This will merge the contents of `<name of branch>` into the current branch. If there are conflicts, the files will be changed by adding `>>>>>>` and `<<<<<<` to highlight where the conflicts occur. You can edit these manually, or use a tool to pick the changes that you want to keep or discard.|
| Delete a branch	| `git branch –D <name of branch>`	| Make sure to switch to another branch before deleting it. Deleting the master branch is not recommended. |

## History

A great feature of git is the ability to look back and see what has being going on in the repo. You can then recover accidentally deleted files, or undo mistakes. Because we use a remote repo to host our files, it's unlikely that reverting to previous commits will be a good thing for you to try, because this will affect the work other people have checked in. In general, if you do something that breaks the build, fix whatever it is, and commit and push another version that resolves it asap. Do not try to revert or reset the master branch.


| Task |	Command line	| Notes |
|------|----------------|-------|
| Look back at what has been committed to the repo | `git log` | Displays the commit logs for all branches in the repo.|
| Look back at what has been committed to the repo, but only for a specific file | `git log –p <file name>` | Displays the commit logs for all branches in the repo related to a specific file. |


## Working with remote repos

Git's strength is allowing multiple people to work in the same repo, even on the same files, at once.

| Task |	Command line	| Notes |
|------|----------------|-------|
| Clone an existing remote repo to your PC | `git clone <name of repo>` | For example: `git clone https://github.com/Microsoft/windows-apps` copies the remote repo to the current directory on your local PC. |
| Download all changes from the remote repo | `git fetch` | Downloads any and all changes between the local and remote repo. However, the changes are not merged and remain in a temporary location. |
| Download all changes from the remote repo and merge them into the current branch | `git pull` | Downloads the changes from the remote repo and merges them. You can specify a branch name. |
| Upload the version of the files in your local repo to the remote repo | `git push` | Publishes your changes.


## When things go wrong

How to deal with a GITA (Git Induced Panic Attack).

| Issue |	Suggestion	|
|------|----------------|
| Avoid breaking the build with a push/sync | Perform a local build before pushing your changes, to avoid the risk of breaking the build. Common ways in which the build breaks are: 1) Broken links to topics. Note that links are case-sensitive. 2) Links to images that are not present or have the wrong file name (again, case sensitive. And check the path.) |
| Your local repo has gone all weird | You can spend time trying to get things back to normal, but unless you think you're going to lose work, it's usually quicker to nuke your LOCAL repo and just create a new repo and clone again. If you have files you want to keep, simply copy them from your local repo first. After closing, you can copy them into the clone you made, and commit the changes. |

