---
author: mijacobs
description: Get set up for authoring WinRT API ref
title: "WinRT API authoring: Markdown and linking"
ms.author: mijacobs
ms.topic: article
ms.prod: windows
ms.technology: uwp
---

# Markdown and linking for API reference

In general, you can use the same markdown for API reference that you use for conceptual markdown articles (such as articles in the **[windows-uwp](https://cpubwin.visualstudio.com/windows-uwp/_git/windows-uwp/)** repo), but there are a few nuances when working with API reference docs. We explain those differences here.

## Links
When linking from one reference article to another within the repo, use relative links.

**Article links from a subdirectory to an article in the root directory:**

    [link text](../article-name.md)

**Article in the root directory links to an article in a subdirectory:**

    [link text](foo-directory/article-name.md)

**Article in a subdirectory links to an article that is in another subdirectory:**

    [link text](../foo-directory/article-name.md)

**Article in a directory links to another article in the same directory:**

    [link text](article-name.md)

When linking to an article outside the documentation directory, use the absolute link to the article or topic. **Remove the *en-us* language locale from the link**.

    [link text](http://azure.microsoft.com/pricing/details/virtual-machines/)

