---
author: mijacobs
description: Contributing to the master branch of the windows-uwp and winrt-api repos
title: Contributing to the master branch of the windows-uwp and winrt-api repos
ms.author: mijacobs
ms.topic: article
ms.prod: windows
ms.technology: uwp
---
# Getting your changes into the master branch of the windows-uwp and winrt-api repos

When you want to publish your contributions to the public site (docs.microsoft.com), you need to get them into the master branch. (For more info on which branch to use when, see [windows-uwp branches](../conceptual/branches.md) and [winrt-api branches](../winrt-api/branches.md).)

To reduce the likelihood of accidentally disclosing pre-release information, you can't merge content directly into the master branch: you need to create a pull request and have that request approved by two writers other than yourself (any two will work).

## Instructions for contributing
**To get your changes into the master branch:**

1. Make your changes in a personal branch based on master. We recommend including "master" in the name of your branch. For example: as "mijacobs/master-layout-edits" or "jimwalk/master-animation-updates".
2. Create a pull request (PR).
3. Have two writers approve your PR.
	Your PR must be approved by two people other than yourself. Add your team to the list of reviewers so they'll get notified about your PR. Use one of these VSTS groups:  **John Kennedy's Team** | **Mark LeBlanc's Team** | **Jill Reinauer's Team** | **Mike Toepke's Team**
4. Complete your PR.
	You can open the PR in Visual Studio Online and click the complete button; or, if you set your PR to auto-complete, this happens automatically.


## Instructions for reviewing

First, make sure that you're receiving PR emails when they go out--they frequently end up in your clutter folder. If you don't want to rely on email, you can also view pull requests waiting for your approval here:

* [windows-uwp open PRs assigned to me](https://cpubwin.visualstudio.com/windows-uwp/_git/windows-uwp/pullrequests?_a=mine)
* [winrt-api open PRs assigned to me](https://cpubwin.visualstudio.com/windows-uwp/_git/winrt-api/pullrequests?_a=mine)

When evaluating the PR, unless the writer specifically asked you to review the content of the articles in the PR, your job is to just make sure that the PR doesn't include information from a pre-release branch. For example, we want to prevent writers from accidentally merging an rs4-based branch into master.

Here are some red flags to watch out for:

* Lots and lots of files

	If the PR shows a large list of changed files, that could indicate that the writer is merging into the wrong branch or the PR branch is old and needs to be updated with the latest version of master. Check with the writer.

* Merge conflicts

	Merge conflicts can happen any time the same file is modified in different branches, but it's more likely to happen when merging into the wrong branch.


## Tips for making your PR go smoothly

* Include the name of your source branch (master) in the name of your personal branch.
* Make sure you do your work in the right branch. If you want your changes to go into master, create a branch based on master.
* Before you create a PR, make sure your branch is clean: merge master into your branch and resolve any merge conflicts.
* When you create the PR, add your team to the list of reviewers so they'll get notified about your PR. Use one of these VSTS groups:  John Kennedy's Team | Mark LeBlanc's Team | Jill Reinauer's Team | Mike Toepke's Team

## FAQ

* **Who can approve my PR?**

	Any writer can approve your PR. We recommend adding the writers on your team to the PR.

* **Who can complete my PR?**

	Any writer can complete your PR--you can even complete your own PRs. In fact, we recommend letting the writer who created the PR complete it. Better yet, writers should set their PR to auto-complete so it gets integrated into master automatically.

* **Why isn't anyone approving my PR?**

	Did you add your team to the list of reviewers? If you did and you still aren't getting a response, your teammates might not know they've been added to the PR. VSTS send an email to each individual that's been added to a PR, but it's likely that email ended up in someone's clutter folder. You might need to send a separate email to your team with a link to the PR.

* **How do I view a list of open PRs?**

	* [windows-uwp open PRs assigned to me](https://cpubwin.visualstudio.com/windows-uwp/_git/windows-uwp/pullrequests?_a=mine)
	* [winrt-api open PRs assigned to me](https://cpubwin.visualstudio.com/windows-uwp/_git/winrt-api/pullrequests?_a=mine)


* **Why can't I just merge my changes directly into master?**

	It's easy to accidentally merge the wrong branch into master (it's happened a few times). Because our master branches are mirrored on github, external developers can see its entire history. So if we accidentally merge a top-secret article into master and then delete it before it goes public, someone who knows what to look for could still find it.




