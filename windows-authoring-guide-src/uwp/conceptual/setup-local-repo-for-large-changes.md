---
author: mattwoj
description: Contribute to UWP conceptual docs.
title: Contribute larger changes in the local Git repo
ms.author: mattwoj
ms.topic: article
ms.prod: windows
ms.technology: uwp
---
# Contribute larger changes in a local Git repository

Setting up a local Git repo for larger changes requires around 15-20 minutes of setup time, but it's way more efficient if you plan on creating or editing lots of content. It also lets you preview content locally. If you have not yet done so, follow the [Get set up for authoring](get-set-up.md) instructions.

This section requires knowledge of the Git version control system. If you are unfamiliar or just want a refresher, please complete the [https://www.codecademy.com/learn/learn-git/](https://www.codecademy.com/learn/learn-git/) tutorial. At a minimum, you need to understand pulling, pushing, branching, and merging.

## What branch should I use for my authoring?

See [Which branch do I use](branches.md) for the list of release branches.

## Personal branches
Rather than working directly in a parent branch, you should create a personal branch off one of the parent branches listed above. Branches are created or selected using the the command line.

### To see what branches you currently have set up on your local machine
- Enter `git branch` in the command line, , a * will appear next to the selected branch. If you recently cloned the repo, you should only see the "master" branch here.
- To change between branches, enter 'git checkout <branch name>'

### To create a new Personal branch from one the parent repo branches
-  `git checkout master`
This selects "master" branch. If you would rather work from a different parent branches (ie. RS3 or Build2017), enter `git fetch origin`, then `git checkout <parent branch name>`. This parent branch will eventually receive your changes.

- `git pull origin master`
This pulls the latest changes from the remote repo (origin) syncing up your local repo with the branch you have selected (in this case the "master" branch). If you are working from a different parent branch, replace "master" with the correct parent branch name.

- `git checkout -b <youralias-parentbranch-description>`
This creates a new personal branch, with a name of your choice, based on the parent branch that you selected in the previous step. We recommend naming your branch using your alias, hyphen, the name of the parent branch, hyphen, a short description of the content change you plan to make in this branch (for example, "mattwoj-RS2-HWAcodesamples").

- You are now ready to [author and add content](#author-and-add-content).

> [!NOTE]
> It is NOT recommended to make changes directly in the Master branch (with exception of correcting small typos). If you have the right permissions, you may be able to work directly in one of the parent branches, but working in a personal branch makes it easier to test your changes and to have them reviewed by others. Also, when your changes eventually make it to the **master** branch and are published, users on github will be able to see your contributions **and** your revision history. If you work in a personal branch, you can **squash** your history when you merge it into one of the parent branches.

### To use an existing Personal branch

To work from a personal branch that already exists remotely: `git fetch origin`, then `git checkout <personal branch name>`. You may also want to ensure that your local and remote personal branches are in sync by entering: `git pull origin <personal branch name>`.

## Author and add content

Authoring changes on your local machine is done with a text editor of your choice. ([Here's a nice comparison article explaining some of the various text editing tools](https://www.codementor.io/mattgoldspink/best-text-editor-atom-sublime-vim-visual-studio-code-du10872i7)).

- After authoring some changes in a text editor, try checking what you have authored by entering `git status` in the command line.

Once you are ready to add your changes to the remote repo so that they will be staged for publishing, enter the following steps in the command line:

- `git add -A`
This command tells git to add ALL of your changes. If you would prefer to only add the changes you have made to one particular file, instead enter the command: `git add <file.md>`, where "file.md" represents the name the file containing your changes.

- `git commit -m “Fixed a few typos”`
This command tells git to commit the changes that you added in the previous step, along with a short message describing the changes that you made.

- `git push -u origin <yourbranchname>`
This command pushes your changes to the remote repo (origin) into the branch that you have specified. The "-u" flag sets the tracking (or "upstream") reference.

After a push to the remote repo, you will be sent an email from *Open Publishing Build Mail* informing whether your contribution built successfully and linking to any error warnings such as broken links, click the links to see your content staged on the site.

To see your branch, go to the [UWP repo branch tab](https://cpubwin.visualstudio.com/_git/windows-uwp/branches?_a=all), find and select your branch.

To see the changes you just pushed in your personal branch on the staging server, go to `https://review.docs.microsoft.com/en-us/windows/uwp/<path to your file>`, then be sure that your branch name is selected in the "Branch" drop-down list on the far right column of the page. For example: [https://review.docs.microsoft.com/en-us/windows/uwp/get-started/universal-application-platform-guide?branch=build2017](https://review.docs.microsoft.com/en-us/windows/uwp/get-started/universal-application-platform-guide?branch=build2017) shows what the "Intro to the Universal Windows Platform" page looks like when staged on the "Build2017" branch.

## Merge your personal branch with its parent when it is ready for publishing

There are two ways to get your updated content into a parent branch (ie. Master for currently live content, RS3, Build, etc).
1) You can merge your own branch with a direct merge.
2) You can create a pull request.

The advantage of a pull request is that it gives a set of reviewers (who you can chose) the chance to review your changes before they become a part of the parent branch published content.

### Perform a direct merge
If you prefer to have your changes reviewed skip to "[Create a Pull Request](#create-a-pull-request)".

`git checkout master` > `git pull origin master`
Once you have looked at your personal branch in the staging site and confirmed that you want the changes to be included in the parent branch (in the case of the master this would go directly in to the live site), you should first be sure that your local repo is in sync with the origin by using the command above. **You can replace "master" with the name of whatever parent branch you are using.*

 `git checkout <yourbranchname>` > `git merge master` *Resolve any merge conflicts*
 Once you have ensured your local master branch is in sync, you can merge (combine) it with your personal branch. If any of the changes you made in the content are in conflict with the same changes that someone else recently made an pushed to the master branch, then you will receive a "merge conflict" which asks you to choose which of the two differing changes you prefer to win the conflict and be included in the live page. [See more about resolving a merge conflict.](https://help.github.com/articles/resolving-a-merge-conflict-using-the-command-line/)

 `git push origin master`
Once you have pushed your content to the master branch of the remote repo, you will receive a new build mail to verify that the branch was built successfully. You can now see your changes on the Master branch of the staging site by going to `https://review.docs.microsoft.com/en-us/windows/uwp/<path to your file>?branch=master`. For example: [https://review.docs.microsoft.com/en-us/windows/uwp/get-started/universal-application-platform-guide?branch=master](https://review.docs.microsoft.com/en-us/windows/uwp/get-started/universal-application-platform-guide?branch=master) shows what the "Intro to the Universal Windows Platform" page looks like when staged on the master branch. **The master branch will published live every workday morning around 9:00am.**

### Create a Pull Request
If you prefer to merge your changes directly, without a review, skip this step and follow the "[Perform a direct merge](#perform-a-direct-merge)" instructions above.

In Git terminology, a review is called a *pull request*, often abbreviated to PR and sometimes called a code review. When you're ready for feedback, it's time to create a pull request:

1. On [https://cpubwin.visualstudio.com/defaultcollection/windows-uwp/_git/windows-uwp/pullrequests](https://cpubwin.visualstudio.com/defaultcollection/windows-uwp/_git/windows-uwp/pullrequests), click the *New pull request* button.
2. Select `<yourbranchname>` relative to `<parentbranch>`.
   For example, set *parentbranch* to **master** if you created your branch from **master**.
3. Edit the title and description
4. Add specific people to review if desired, you can also add a VSO task ID to the "Work Items" if desired
5. Click the *New pull request* button

VSTS will send an email to everyone on the pull request. They can comment on your changes and choose to sign off or ask for revisions. [See more on how to review a pull request](../../managing-contributions/review-pull-requests.md) -- you could consider sharing these instructions with anyone that you have asked to help with a review that you believe could benefit from some instruction on how to do so.

### Responding to PR reviewer comments

You can respond to the comments that reviewers have made on your Pull Request on the [VSTS repo](https://cpubwin.visualstudio.com/defaultcollection/windows-uwp/_git/windows-uwp/pullrequests?_a=active). If you need to make changes in response to feedback:

1. Make necessary revisions to your local files with a text editor
2. Create a new commit in your personal branch
3. Use `git push` to publish the new commit containing your revisions

Once the new commit is published, VSTS sends a new email to the reviewers. You can also consider replying on the comments section of your Pull Request linked above.

### Completing a pull request

Once your PR is signed off on by your chosen reviewers, your updates will automatically be published to the live site. For the master branch, this is every workday morning around 9am. For other parent branches, the branch name should indicate the timing of when the branch will be published live... so Build2017 will be published with all of the Build conference content (somewhere around May 10th).
