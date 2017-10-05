---
author: mattwoj
description: Making and reviewing changes
title: "Edge Dev Docs authoring: Making and reviewing changes"
ms.author: mattwoj
ms.topic: article
ms.prod: windows
ms.technology: microsoft-edge
---

# Making and reviewing a change

This section requires knowledge of the Git version control system. If you are unfamiliar or just want a refresher, please complete the [https://www.codecademy.com/learn/learn-git/](https://www.codecademy.com/learn/learn-git/) tutorial. At a minimum, you need to understand pulling, pushing, branching, and merging.

## Configuring Git

If this is the first time you've installed Git on a new machine, you need to configure Git by giving it your name and email address. **This only needs to be done once**. You can read more details [here](https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup).

```cmdprompt
C:\gitrepos\edge-developer>git config --global user.name "Your Name"

C:\gitrepos\edge-developer>git config --global user.email youralias@microsoft.com
```

## Working in a personal branch

In the Git workflow, changes are made in a personal branch. This is done from the command line.

1. Use the `checkout` command to switch to one of the main branches. This will be the branch you merge your work back into after you're done. For info on which branch to use, see [branches](branches.md).

	```cmdprompt
	C:\gitrepos\edge-developer>git checkout vNext
	```
This main branch will be the parent of your personal branch, and it's the branch that will eventually receive your changes.
2. Sync to the latest version of the Git repository to your PC using `git pull -p`:

	```cmdprompt
	C:\gitrepos\edge-developer>git pull -p
	Already up-to-date.
	```
3. Create your branch:

	```cmdprompt
	C:\gitrepos\edge-developer>git checkout -b youralias-parentbranch/my-first-change
	Switched to the branch 'youralias-parentbranch/my-first-change
	```
The branch naming convention makes it easy to see who is working on what. Be descriptive. For example, `mattwojo-develop/bug-fixes-for-tile-how-to`.

## Editing a file

1. Use the checkout command to switch to your personal branch, if you haven't already.

	```cmdprompt
    C:\gitrepos\edge-developer>git checkout youralias-parentbranch/my-first-change
	Switched to the branch 'youralias-parentbranch/my-first-change
	```
2. Open the markdown file you want to edit. You can use any text editor.

Here's a sample file:

```markdown
---
author: abbycar
title: Edge extensions
description: This section discusses how to build extensions for the Microsoft Edge browser.
ms.author: abigailc
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: microsoft-edge
keywords: edge, extensions
---
#  Guides

## Accessibility
To ensure your extension's icon is visible while in both light and dark mode, follow the [accessibility](./guides/accessibility.md) guide.

## Adding and removing extensions
Learn how to [add and remove extensions](./guides/adding-and-removing-extensions.md), as well as move an extension's button next to the address bar.

## Creating an extension
Get started with [creating extensions](./guides/creating-an-extension.md) by following a couple tutorials and learning the basics.

## Debugging extensions
With F12 Developer Tools, learn [how to debug an extension](./guides/debugging-extensions.md)'s background script, content scripts, and extension pages.

## Design
Learn about the [design](./guides/design.md) aspects of extensions including the various icon sizes you need and where these icons appear.

## Internationalization
Make your extension accessible for different languages and test your language strings with the [internationalization](./guides/internationalization.md) guide.


| Topic | Description|
|-------|------------|
| [Porting Chrome extensions](./guides/porting-Chrome-extensions.md) | See how to easily port your Chrome extension using the Microsoft Edge Extension Toolkit. |
| [Packaging](./guides/packaging.md) | Once you've completed your extension, learn about the final steps needed to package it. |


> [!NOTE]
> Submitting a Microsoft Edge extension to the Windows Store is currently a restricted capability. [Reach out to us](http://aka.ms/extension-request) with your requests to be a part of the Windows Store, and we’ll consider you for a future update.