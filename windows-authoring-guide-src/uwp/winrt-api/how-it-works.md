---
author: mijacobs
description: Get set up for authoring WinRT API ref
title: "WinRT API authoring: How the system works"
ms.author: mijacobs
ms.topic: article
ms.prod: windows
ms.technology: uwp
---

# How the WinRT API authoring system works

In the **winrt-api repo**, there's a folder for each namespace. Inside each namespace folder, there's a file for each type and member in that namespace. For example, here are the markdown files for the Windows.ApplicationModel.AppInfo class.

<ul>
<li>\winrt-api
<ul>
    <li>windows.applicationmodel
        <ul>
            <li>appinfo.md</li>
            <li>appinfo_appusermodelid.md</li>
            <li>appinfo_displayinfo.md</li>
            <li>appinfo_id.md</li>
        </ul>
    </li>
<!--
    <li>windows.applicationmodel.activation</li>
    <li>...</li>
-->
</ul></li>
</ul>

Each markdown file contains sections for the API description, remarks, and examples. When you change a file, the system takes the content in each markdown file, adds additional information from the **API catalog**, and combines the individual markdown files into a single file for each class, interface, structure, and delegate. For example, here's what the published version of the AppInfo class looks like: [https://docs.microsoft.com/uwp/api/windows.applicationmodel.appinfo](https://docs.microsoft.com/uwp/api/windows.applicationmodel.appinfo).

In addition to the **winrt-api** internal repo, there's a github mirror of the repo here: [https://github.com/MicrosoftDocs/winrt-api/blob/docs/](https://github.com/MicrosoftDocs/winrt-api/blob/docs/). This repo contains the public version of the master branch of the **winrt-api** repo. External developers can submit pull requests to this repo. When the pull requests are accepted, their contributions are eventually integrated back into the **winrt-api** repo.
