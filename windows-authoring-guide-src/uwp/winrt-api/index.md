---
author: mijacobs
description: Contribute to UWP API reference docs.
title: Authoring WinRT API reference
ms.author: mijacobs
ms.topic: article
ms.prod: windows
ms.technology: uwp
---
# Writing UWP/WinRT API reference

Windows UWP/WinRT API reference docs are located in the **winrt-api repo**: [https://cpubwin.visualstudio.com/windows-uwp/_git/winrt-api](https://cpubwin.visualstudio.com/windows-uwp/_git/winrt-api).

> [!NOTE]
> To view a tutorial video on contributing using the web interface, click [here](https://microsoft.sharepoint.com/sites/infopedia/Media/details/aevd-3-119693).

## Where can I view content?
- [Windows UWP/WinRT API Ref staging site](https://aka.ms/winrtdocs)
*(You can change which repo branch you are viewing in this staging environment.)*
- [Windows UWP/WinRT API Ref live site](https://docs.microsoft.com/en-us/uwp/api/)

The instructions in this section apply only to WinRT/UWP apis. Other APIs, such as win32, are not yet in our markdown system.

> [!NOTE]
> We provide public access to the [master](branches.md) branch of the **winrt-api** repo. That means that the source code of your articles--including HTML comments, commit comments, and revision history--will be visible to external developers. Articles in the rs3 branch will eventually trickle down to the master branch, when it's time to publish them. Please plan accordingly.

## Who can contribute?
Anyone at Microsoft can contribute to the documentation. If, for some reason, you don't have access to the repo, please contact [wdgapiref](mailto:wdgapiref@microsoft.com).


## How do I contribute?
You can contribute through the web interface, or by setting up a local git repository.

For a quick-start, watch [this video](https://microsoft.sharepoint.com/sites/infopedia/Media/details/aevd-3-119693) that walks you through the web interface contribution method.


### Use the web interface

- Go to the staging server, [https://aka.ms/winrtdocs](https://aka.ms/winrtdocs)
- Navigate to the API of interest.
- You'll notice  there is an **Edit** button for each member in a class.
- Click the edit button for the member you want to modify.
- The edit button takes you to the web interface for the **winrt-api repo**: [https://cpubwin.visualstudio.com/windows-uwp/_git/winrt-api](https://cpubwin.visualstudio.com/windows-uwp/_git/winrt-api)

You don't have to install anything to use the web interface. It's good for making small changes. If you go with this approach, you should still read the [Which branch do I use?](branches.md) article.

### Set up a local git repository
You can also use git locally and clone the repo. This approach requires around 15-20 minutes of setup time, but it's way more efficient if you plan on creating or editing lots of content. It also lets you preview content locally.

1. [Get set up](get-set-up.md)
2. [Which branch do I use?](branches.md)
3. [Making and reviewing changes](making-and-reviewing-changes.md)
4. [Markdown for API ref](markdown-for-api-ref.md)

For cpub writers only:
* [Adding, removing, changing, and holding back APIs](diff.md)

## System Bugs and Enhancements
If you encounter any bugs/issues in the system or if you have any enhancement suggestions, please send email to [wdgapiref](mailto:wdgapiref@microsoft.com) with a description of the bug or enhancement. If you're reporting a bug, please include repro steps and pointers to all related content files and sample output, as appropriate.
