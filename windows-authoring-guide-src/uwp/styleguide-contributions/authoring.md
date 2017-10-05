---
author: mijacobs
ms.author: mijacobs
ms.topic: article
ms.prod: windows
ms.technology: uwp
pm-contact: chigy
---
# You were assigned a guidance doc bug, now what?

For one reason or another, you were assigned a documentation bug. There are mainly 3 different processes depending on types of change being asked of you:
1. [Simple bug fix process](#bug-fix)
2. [Update process](#update)
3. [Fluent Design System process](#fluent)

**For all of the above type, please follow the instruction in [Writing UWP conceptual ("how-to") docs](../conceptual/index.md) to set up your environment.**

## Simple bug fix process <a name="bug-fix">
This section is applicable for update of the guidance documentation that has already been published. You are making minor update to the guidance to fix issues.
When the bug fix is submitted, it will be reviewed by the applicable reviewer that are part of Fluent Design System process to ensure the updates adhere to the Fluent story.

### Branches
If you are working on articles that are not yet public, please follow instruction outlined in other two processes. For simple bug fix process, please update **[master branch](https://cpubwin.visualstudio.com/windows-uwp/_git/windows-uwp/?branch=flight)**

For more information about the branching system and how to set one up, please read [Windows-UWP release branches](../conceptual/branches.md) article.

## Update or creation process not being tracked by Fluent Design System process <a name="update">
If you are making an update to existing article or creating a new article that is not strictly tracked by Fluent Design System process, please follow the process here. While it might not be tracked strictly through Fluent Design System process, the article will be reviewed by the applicable reviewer that are part of Fluent Design System process to ensure the updates adhere to the Fluent story.

### Branches
Please identify the proper branch to use based on what your intentions are:
- **[master](https://cpubwin.visualstudio.com/windows-uwp/_git/windows-uwp/?branch=flight)**: Articles for features that are available to developers today. This is appropriate for articles that are already published and you are making changes to it that is not depended on new features that are yet released. This branch is published daily. 
- **[rs3](https://cpubwin.visualstudio.com/windows-uwp/_git/windows-uwp/?branch=rs3)**: Articles for features that are being held back until RS3 RTM. This is appropriate for articles written for features that is shipping as part of RS3 SDK. 
- **[neon-design-system](https://cpubwin.visualstudio.com/windows-uwp/_git/windows-uwp/?branch=neon-design-system)**: Use this branch for internal-only articles that won't be published externally. This is appropriate for articles that will never ship to external customers or the feature is not currently officially planned to ship in RS3 (e.g. RS4 articles, future incubation ideas, etc.)  

For more information about the branching system and how to set one up, please read [Windows-UWP release branches](../conceptual/branches.md) article.

### File name tagging
There should be no tagging on file names for articles going out in **master** and **rs3** branches.
Follow Fluent Design System process's instruction for **neon-design-system** branch.

## Fluent Design System process <a name="fluent">
This process will be tracked very closely through Fluent Design Planning process because one of the exit criterion of Fluent Design System planning process before it can be passed onto engineering process is internally published guidance documentation.

### The process
For complete process authors are to follow for Fluent design system related articles, please visit [Publishing and announcing Fluent design system articles](publishing-and-announcing.md)

### Branches
Assuming almost all the features being tracked for Fluent Design System process are new functionality that has not yet shipped or it is being planned to ship in the next release cycle, the correct branch to use is **[neon-design-system](https://cpubwin.visualstudio.com/windows-uwp/_git/windows-uwp/?branch=neon-design-system)**.

For more information about the branching system and how to set one up, please read [Windows-UWP release branches](../conceptual/branches.md) article.

### File name tagging
In order to ensure the files go through proper channels and does not fall through cracks, please use the following naming convention:
- If the feature is currently in your official engineering plan for RS4, add **-rs4.md**
- If the feature is going out at some future timeframe but release is not yet officially known, add **-rsfuture.md**
- If the article is internal only and should never publish (perhaps this article frames the work to follow but article itself is not interesting externally), do not add any suffix.

Next article: [Publishing and announcing work](publishing-and-announcing.md)