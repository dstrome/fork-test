---
author: mijacobs
description: Making and reviewing changes
title: "WinRT API authoring: Making and reviewing changes"
ms.author: mijacobs
ms.topic: article
ms.prod: windows
ms.technology: uwp
---

# Making and reviewing a change

This section requires knowledge of the Git version control system. If you are unfamiliar or just want a refresher, please complete the [https://www.codecademy.com/learn/learn-git/](https://www.codecademy.com/learn/learn-git/) tutorial. At a minimum, you need to understand pulling, pushing, branching, and merging.

## Configuring Git

If this is the first time you've installed Git on a new machine, you need to configure Git by giving it your name and email address. **This only needs to be done once**. You can read more details [here](https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup).

```cmdprompt
C:\VSTS\winrt-api>git config --global user.name "Your Name"

C:\VSTS\winrt-api>git config --global user.email youralias@microsoft.com
```

## Working in a personal branch

In the Git workflow, changes are made in a personal branch. This is done from the command line.

1. Use the `checkout` command to switch to one of the main branches. This will be the branch you merge your work back into after you're done. For info on which branch to use, see [branches](branches.md).

	```cmdprompt
	C:\VSTS\winrt-api>git checkout rs2
	```
This main branch will be the parent of your personal branch, and it's the branch that will eventually receive your changes.
2. Sync to the latest version of the Git repository to your PC using `git pull -p`:

	```cmdprompt
	C:\VSTS\winrt-api>git pull -p
	Already up-to-date.
	```
3. Create your branch:

	```cmdprompt
	C:\VSTS\winrt-api>git checkout -b youralias-parentbranch/my-first-change
	Switched to the branch 'youralias-parentbranch/my-first-change
	```
The branch naming convention makes it easy to see who is working on what. Be descriptive. For example, `mijacobs-rs2/bug-fixes-for-tile-apis`.

> [!NOTE]
> If you have the right permissions, you don't *have* to work in a personal branch--you can work directly in one of the main branches. But working in a personal branch makes it easier to test your changes and to have them reviewed by others. Also, when your changes eventually make it to the **master** branch and are published, users on github will be able to see your contributions **and** your revision history. If you work in a personal branch, you can **squash** your history when you merge it into one of the main [branches](branches.md).

## Editing a file

1. Use the checkout command to switch to your personal branch, if you haven't already.

	```cmdprompt
    C:\VSTS\winrt-api>git checkout youralias-parentbranch/my-first-change
	Switched to the branch 'youralias-parentbranch/my-first-change
	```
2. Open the markdown file you want to edit. You can use any text editor.

In the **winrt-api repo**, there's a folder for each namespace. Inside each namespace folder, there's a file for each type and member in that namespace. For example, here are the markdown files for the Windows.ApplicationModel.AppInfo class.

<ul>
<li>\winrt-api
<ul>
    <li>windows.applicationmodel
        <ul>
            <li>appinfo.md</li>
            <li>appinfo_appusermodelid.md</li>
            <li>appinfo_displayinfo.md</li>
            <li>appinfo_id.md</li>
        </ul>
    </li>
<!--
    <li>windows.applicationmodel.activation</li>
    <li>...</li>
-->
</ul></li>
</ul>

Each markdown file contains sections for the API description, remarks, and examples. Here's a sample file:

```markdown
---
-api-id: T:Windows.ApplicationModel.AppDisplayInfo
-api-type: winrt class
---

<!-- Class syntax.
public class AppDisplayInfo : Windows.ApplicationModel.IAppDisplayInfo
-->

# Windows.ApplicationModel.AppDisplayInfo

## -description
Provides an application's name, description, and logo.

## -remarks
This class can be used to get information about applications that are registered as protocol handlers. You can get an instance of this class from [AppInfo.DisplayInfo](appinfo_displayinfo.md).

## -examples

## -see-also
```

> [!IMPORTANT]
> Don't change or remove section headers that begin with a "-", such as "## -description" or "## -see-also". You can modify the contents of these sections, but don't change the section headers themselves--the system expects them to be there.

When you change a file, the system takes the content in each markdown file, adds additional information from the **API catalog**, and combines the individual markdown files into a single file for each class, interface, structure, and delegate. For example, here's what the published version of the AppInfo class looks like: [https://docs.microsoft.com/uwp/api/windows.applicationmodel.appinfo](https://docs.microsoft.com/uwp/api/windows.applicationmodel.appinfo).


## Viewing your changes
[UPDATE: the limitation described below is now lifted. But commit and push *to your branch* before coming back here to preview it.]

Right now, the only way to view an accurate rendering of your changes is to get your work back into one of the main branches, and then going to
`https://review.docs.microsoft.com/uwp/api/?branch=branchname`, where *branchname* is **master**, **flight**, or **rs2**. For example, here's the staging location for rs2 content:

[https://review.docs.microsoft.com/uwp/api/?branch=rs2](https://review.docs.microsoft.com/uwp/api/?branch=rs2)


We'll be fixing this limitation within the next month, at which point there will be staging previews for all personal branches.

In the meantime, follow the instructions in the next sections to get your content into a main branch for staging.

## Committing work to your branch

After making some changes, take a snapshot of your work by creating a Git *commit*. Here's a sample workflow:

```cmdprompt
C:\VSTS\winrt-api>git branch
  master
* youralias-parentbranch/my-first-change

C:\VSTS\winrt-api>git status
On branch youralias-parentbranch/my-first-change
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   windows.applicationmodel/appdisplayinfo.md

no changes added to commit (use "git add" and/or "git commit -a")

C:\VSTS\winrt-api>git add windows.applicationmodel/appdisplayinfo.md

C:\VSTS\winrt-api>git status
On branch youralias-parentbranch/my-first-change
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        modified:   windows.applicationmodel/appdisplayinfo.md


C:\VSTS\winrt-api>git commit -m "Your commit message here"
[youralias/my-first-change 9b6ecaa] Your commit message here
 1 file changed, 1 insertion(+), 1 deletion(-)
```

Commit messages can be multi-line. Just hit `<ENTER>` before the closing quote.

You now have a *local* commit. Make as many as you find useful. Keep in mind that local commits only exist on your PC, no one else can see them. In the next section, you'll learn how to review your changes with others.

## Publishing work to your branch

After you've committed your changes, you should publish them to your branch. Branch publishing is useful for:

* Backing up your work in case your PC dies
* Working from multiple computers
* Getting ready to review

To publish your branch, first check to make sure you're in the correct, branch, then use `git push --set-upstream origin youralias-parentbranch/my-first-change`.

```cmdprompt
C:\VSTS\winrt-api>git branch
  master
  rs2
* youralias-parentbranch/my-first-change

C:\VSTS\winrt-api>git push --set-upstream origin youralias/my-first-change
Total 0 (delta 0), reused 0 (delta 0)
To https://cpubwin.visualstudio.com/defaultcollection/windows-uwp/_git/winrt-api
 * [new branch]      youralias/my-first-change -> youralias/my-first-change
Branch youralias/my-first-change set up to track remote branch youralias/my-first-change from origin.
```
>[!NOTE]
> You only need to run `git push --set-upstream origin youralias/my-first-change` once per branch. To push additional changes, you can simply use `git push`:
```cmdprompt
C:\VSTS\winrt-api>git push
```

## Getting your content into a main branch
There are two ways to get your updated content into a main branch. You can merge your branch yourself, or you can create a pull request. The advantage of a pull request is that it gives a set of reviewers (whom you can choose) the chance to review your changes before they become a part of the main branch.

### Perform a direct merge
If you have elevated permissions and your changes don't need reviewed, you can merge your personal branch directly into its parent branch.

<ol>
<li><b>Make sure all of your changes have been committed and pushed to personal branch (see the previous section, [Publishing work to your branch](#publishing-work-to-your-branch)).</b>
</li>
<li>Sync your personal branch.
<div>
<pre><code>
C:\VSTS\winrt-api>git checkout youralias-parentbranch/my-first-change
C:\VSTS\winrt-api>git pull -p
</code></pre>
</div>
</li>
<li>Re-sync your personal branch with its parent branch. This step isn't  required, but it can make the merge operation easier.
<div>
<pre><code>
C:\VSTS\winrt-api>git fetch origin
C:\VSTS\winrt-api>git rebase -p origin/parentbranch
</code></pre>
</div>
(where *parentbranch* is the parent branch of your personal branch: **rs2**, **flight**, or **master**)
If there are potential merge conflicts, you'll be notified at this point. After you're done, push your changes.
<div>
<pre><code>
C:\VSTS\winrt-api>git push
</code></pre>
</div>
</li>
<li>Switch to the parent branch and merge.
<div>
<pre><code>
C:\VSTS\winrt-api>git checkout parentbranch
C:\VSTS\winrt-api>git merge youralias-parentbranch/my-first-change
</code></pre>
</div>
If there are merge conflicts, you'll be notified. After resolving them, push your updates.
<div>
<pre><code>
C:\VSTS\winrt-api>git push
</code></pre>
</div>
</li>
</ol>


### Creating a pull request

In Git terminology, a review is called a *pull request*, often abbreviated to PR and sometimes called a code review. When you're ready for feedback, it's time to create a pull request:

1. On [https://cpubwin.visualstudio.com/defaultcollection/windows-uwp/_git/winrt-api/pullrequests](https://cpubwin.visualstudio.com/defaultcollection/windows-uwp/_git/winrt-api/pullrequests), click the *Create pull request* button.
2. Select `youralias-parentbranch/my-first-change` relative to `parentbranch`.
   For example, set *parentbranch* to **master** if you created your branch from **master**, and set it to **rs2** if you created your branch from **rs2**.
3. Edit the title and description
4. Add specific people to review if desired
5. Click *Create pull request*

VSTS will send an email to everyone on the pull request. They can comment on your changes and choose to sign off or ask for revisions.

> **Coming soon: **
> Reviews will be able to preview your article when they review your pull request. In the meantime, reviewers have to evaluate the raw markup.

### Responding to comments

You can respond to VSTS comments on the website. If you need to make changes in response to feedback:

1. Make necessary revisions to the files your PC
2. Create a new commit in your branch (`youralias-parentbranch/my-first-change`)
3. Use `git push` to publish your new commit

Once the new commit is published, VSTS sends a new email to the reviewers.

### Handling merge conflicts

Sometimes VSTS will alert you that there are *merge conflicts* that need to be resolved before your pull request can be completed. This can happen if a file you were working on was changed by someone else in the parent branch. Merging is covered by the Git Teamwork section of the tutorial you completed previously (https://www.codecademy.com/learn/learn-git/). The typical workflow is to switch to master, sync it, switch back to your branch, merge the parent branch into your branch, finally manually resolving conflicts.

```cmdprompt
C:\VSTS\designstudio.windowsstyleguide>git checkout rs2

C:\VSTS\winrt-api>git pull -p
Updating c018055..5c4e7da
Fast-forward
 winrt-api/index.md       | 17 ++++++++++--
 winrt-api/system.applicationmodel.appinfo.md | 48 +++++++++++++++++++++++++++++++++
 2 files changed, 63 insertions(+), 2 deletions(-)

C:\VSTS\winrt-api>git checkout youralias-parentbranch/my-first-change
Switched to branch 'youralias-parentbranch/my-first-change'

C:\VSTS\winrt-api>git merge rs2
```


> **Merge carefully!** You can end up deleting other people's changes.


### Completing a pull request

Once your PR is signed off, take one last close look at the files you've changed and verify nothing was unintentionally changed (usually by a bad merge). Finally, ask the CPUB area owner to complete your PR. They will be automatically added to your PR as a *required* reviewer and will have signed off.

When a CPUB owner completes your PR, they will delete `youralias/my-first-change` from the server. You need to switch back to the `master` (or `rs2` or `rs3`) branch, sync it, then delete `youralias/my-first-change`.

```cmdprompt
C:\VSTS\winrt-api>git checkout master
Switched to branch 'master'
Your branch is behind 'origin/master' by 1 commit, and can be fast-forwarded.
  (use "git pull" to update your local branch)

C:\VSTS\winrt-api>git pull -p
Updating c018055..5c4e7da
Fast-forward
 gulp_helpers/gulp-handlebars-to-html.js | 17 ++++++++++--
 gulp_helpers/sitemap-helper.js          | 48 +++++++++++++++++++++++++++++++++
 2 files changed, 63 insertions(+), 2 deletions(-)

C:\VSTS\winrt-api>git branch -d youralias/my-first-change
Deleted branch youralias/my-first-change (was c018055).

C:\VSTS\winrt-api>git branch
* master
```


**Next: [Markdown for API ref](markdown-for-api-ref.md)**