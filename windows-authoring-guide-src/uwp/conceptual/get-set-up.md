---
author: mattwojo
description: Set up UWP conceptual repo.
title: UWP Conceptual repo set up
ms.author: mattwoj
ms.topic: article
ms.prod: windows
ms.technology: uwp
---

# Get set up for contributing to UWP Conceptual documentation 

If you are setting up git authoring for the first time, follow the instructions to [Set up a GitHub account](../../github-account.md) before following the steps below to set up the repo.

## Set up a local repo for the UWP Conceptual content
1. Open the Git Command Prompt: Click the Start menu and type **Git CMD**, this will pop open the command prompt with C:\Users\yourname>
2. C:\Users\yourname> `mkdir C:\VSTSrepos\` 
*("VSTSrepos" is the name of the folder where VSTS  Git repos are kept, feel welcome to name this whatever you prefer)*
3. `cd C:\VSTSrepos\` (open the folder you created)
4. `git clone https://cpubwin.visualstudio.com/windows-uwp/_git/windows-uwp` 
   	The system creates a local clone on your machine. The process typically takes ~5 minutes.
5. `cd C:\VSTS\windows-uwp` (now you are inside of your local UWP conceptual repo folder and can see the files with a `dir` or `ls` command)

You are now ready to start authoring.

Next steps:
- [Which branch should you use?](branches.md)
- [Contribute larger changes in a local Git repository](setup-local-repo-for-large-changes.md)
- [Contribute small changes with the web interface](/web-interface-for-small-contributions.md)
