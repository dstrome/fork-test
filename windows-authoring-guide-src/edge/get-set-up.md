---
author: mattwojo
description: Get set up for authoring Edge Dev Docs 
title: Edge docs authoring set up
ms.author: mattwoj
ms.topic: article
ms.prod: windows
ms.technology: microsoftedge
---

# Get set up for contributing to Microsoft Edge Developer documentation

If you are setting up git authoring for the first time, follow the instructions to [Set up a GitHub account](../github-account.md) before following the steps below to set up the repo.

## Set up a local repo for Microsoft Edge Docs content
1. Open the Git Command Prompt: Click the Start menu and type **Git CMD**, this will pop open the command prompt with C:\Users\yourname>
2. C:\Users\yourname> `mkdir C:\GitHubrepos\` 
*("GitHubrepos" is the name of the folder where your GitHub docs content is kept, feel welcome to name this whatever you prefer)*
3. `cd C:\GitHubrepos\` (open the folder you created)
4. `git clone https://github.com/MicrosoftDocs/edge-developer.git`
    	This will create a local clone of the repo on your machine where you can do your authoring and then push back to the remote repo.
5. `cd C:\GitHubrepos\edge-developer`
You are now inside of your local Edge docs repo folder and can see the files with a `dir` or `ls` command. 

You are now ready to start authoring.

Next steps:
- [Writing Microsoft Edge docs](index.md)
- [Which branch should you use?](branches.md)
- [Making and reviewing a change](making-and-reviewing-changes.md)
