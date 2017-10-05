---
author: mijacobs
description: Get set up for authoring WinRT API ref
title: "WinRT API authoring: Branching"
ms.author: mijacobs
ms.topic: article
ms.prod: windows
ms.technology: uwp
---

# Branching in the winrt-api repo

The [winrt-api repo](https://cpubwin.visualstudio.com/windows-uwp/_git/winrt-api) has three main branches.

## Main branches


+ **[rs2](https://cpubwin.visualstudio.com/windows-uwp/_git/winrt-api/?branch=rs2)**: The latest API reference for the latest build from main.
+ **[flight](https://cpubwin.visualstudio.com/windows-uwp/_git/winrt-api/?branch=flight)**: API reference from the latest approved flight. There’s a new flight every 2 weeks. This branch serves as a staging area where we can stabilize the docs before pushing them to master. In general, you won't have to interact with this branch; our project administrators will maintain it and reach out to individual writers if they need help resolving a merge conflict or investigating an issue.
+ **[master](https://cpubwin.visualstudio.com/windows-uwp/_git/winrt-api/?branch=master)**: The docs that are live on Docs.Microsoft.com.

## Which main branch do I use?
In general, you should work out of the **rs2** branch (or a personal branch created off **rs2**).

<ul>
<li><b>Updates to public APIs</b>
If you want to update an API that's already public, and you want the update to be visible within 24 hours, update the **master** branch. The project administrator will merge your updates into the other branches (**flight** and **rs2**) as well.</li>
<li><b>Diffing: Adding and deleting new APIs</b>
Use the **rs2** branch for diffing. For more information on diffing, see [Adding, removing, and holding back APIs](diff.md).</li>
<li><b>Authoring new APIs</b>
Use the **rs2** branch for authoring new APIs that haven't been released yet. If the API is pre-release but has already been published on the dev center, you can author it in **master** or **rs2**. If you author your updates in **master**, your updates will go live sooner; updates to **rs2** won't be published until the next flight is released, which might be 2 weeks.</li>
</ul>


## Personal branches
Rather than working directly in a main branch, you should create a personal branch off one of the main branches. The exception is diffing--we recommend making your diff changes directly into the **rs2** branch. Instructions for creating personal branches are covered in the next section, [Making and reviewing changes](making-and-reviewing-changes.md).

**Next: [(For cpub writers) Adding, removing, changing, and holding back APIs](diff.md)**

**Next: [(For everyone else) Making and reviewing changes](making-and-reviewing-changes.md)**
