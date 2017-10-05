---
author: mijacobs
description: Get set up for authoring WinRT API ref
title: "WinRT API authoring: Get set up"
ms.author: mijacobs
ms.topic: article
ms.prod: windows
ms.technology: uwp
---

# Get set up for contributing to UWP API ref documentation

If you are setting up git authoring for the first time, follow the instructions to [Set up a GitHub account](../../github-account.md) before following the steps below to set up the repo.


## Set up a local repo for the UWP API ref content
1. Open the Git Command Prompt: Click the Start menu and type **Git CMD**, this will pop open the command prompt with C:\Users\\ &lt; yourname &gt;
2. C:\Users\\ &lt; yourname &gt; `mkdir C:\VSTSrepos\`
*("VSTSrepos" is the name of the folder where VSTS Git repos are kept, feel welcome to name this whatever you prefer)*
3. `cd C:\VSTSrepos\` (open the folder you created)
4. `git clone https://cpubwin.visualstudio.com/windows-uwp/_git/winrt-api`
   	The system creates a local clone on your machine. The process typically takes ~5 minutes.
5. `cd C:\VSTS\winrt-api` (now you are inside of your local UWP API ref repo folder and can see the files with a `dir` or `ls` command)

You are now ready to start authoring.

**Next: [Which branch should you use?](branches.md)**
