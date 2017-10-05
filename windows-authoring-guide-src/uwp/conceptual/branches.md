---
author: mijacobs
description: Contribute to UWP conceptual docs.
title: Which branch should I use? (UWP conceptual)
ms.author: mijacobs
ms.topic: article
ms.prod: windows
ms.technology: uwp
---

# Which branch should I use?

Our git repo has a lot of branches; many of these are personal branches that you can ignore. When you're ready to make a change or write a new article, create your own personal branch based off one of the release branches.

## Windows-UWP release branches
The [windows-uwp repo](https://cpubwin.visualstudio.com/windows-uwp/_git/windows-uwp) has several release branches:

- **[master](https://cpubwin.visualstudio.com/windows-uwp/_git/windows-uwp/?branch=flight)**: Articles for features that are available to developers today. This branch is published daily.
- **[rs3](https://cpubwin.visualstudio.com/windows-uwp/_git/windows-uwp/?branch=rs3)**: Articles for features that are being held back until RS3 RTM.
- **[neon-design-system](https://cpubwin.visualstudio.com/windows-uwp/_git/windows-uwp/?branch=neon-design-system)**: Use this branch for internal-only articles that won't be published externally.

To make an update, you create a personal branch based on one of these release branches--you don't work out of release branches directly.

For content that can be published right away, work out of a personal branch created off **master**. For content that should be held back until a specified release date, choose the branch associated with the release you would like your contribution to be included in.

## Instructions for creating a personal branch

When you create a personal branch, it's a good idea to include your alias and the name of the parent branch. For example, "mijacobs/master-nav-updates" or "mijacobs/rs3-button-updates".

You can create a personal branch using the command-line/local repo or using the web interface:

* [Create a personal branch via the command-line/local repo](setup-local-repo-for-large-changes.md)
* [Create a personal branch using the web interface](web-interface-for-small-contributions.md)

## Frequently asked questions

* <span style="color: darkOrange">I created a personal branch off based on the rs3 release branch, but it turns out that my article can go public. Can I merge my branch into master?</span>

	No! Merging your branch doesn't just merge your new article, it will merge everything that existed in rs3 into master as well! Merge your article back into its parent branch, rs3, and then contact [The WDG OP scrum team](mailto:wdgopscrum@microsoft.com) for help moving your article to master.

* <span style="color: darkOrange">I have an article for an rs3 feature, but it can go public soon. What branch should I use?</span>

	Create a personal branch off master. When the feature is available, merge your branch into master to publish it.

## Related articles

* [Git branching - Branches in a nutshell](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell)