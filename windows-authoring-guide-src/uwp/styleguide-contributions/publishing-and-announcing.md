---
author: mijacobs
ms.author: mijacobs
ms.topic: article
ms.prod: windows
ms.technology: uwp
pm-contact: chigy
---
# Publishing and announcing Fluent design system articles

In order for Fluent guidance vTeam to work seamlessly with ever growing numbers of authors, we have a set process we ask authors to follow. This way, everyone is aware of the expectations and steps which makes it easier to quality control, get the appropriate reviewers lined up, etc.

At high level, the work flow is as follows:
1. [Identifying the topic](#topic)
2. [Documentation bug is opened and assigned to an author](#bug-open)
3. [Writing the article](#writing)
4. [Creating draft doc and kicking off reviewing process](#review-process)
5. [Sending the 'announcement' to uwpcpnews](#announcement)
6. [Don't forget to resolve the bug](#bug-resolve)

## Identifying the topic <a name="topic">
Anything we publish as Microsoft which impacts UX (interaction, visual, motion, usability, etc.) need to adhere to Fluent Design System principles and beliefs. While it is ambitious goal, we are starting piece by piece. The first pieces we are dedicating our time and effort are the topics we cover in Fluent planning waves. As such, any work that is part of Fluent planning will go through this process.

## Documentation bug is opened and assigned to an author <a name="bug-open">
Once we have an idea of the topic we want to add to the guidance, a documentation bug is created and assigned to an intended author. Author needs to ensure that he/she is the right owner and let [chigy](mailto:chigy@microsoft.com) know if there is any assignment in error.

For more information on branches and how you need to set up the authoring environment, please visit [You were assigned a guidance doc bug, now what?](authoring.md)

## Writing the article <a name="writing">
You can either write the article directly in markdown or if you prefer, writer in Word doc format. Different authors has different levels of writing skills and it is OK. Please let the [ddeppub](mailto:ddeppub@microsoft.com) know if you would like additional writing help or any other help you require to be successful.

## Kicking off reviewing process <a name="review-process">
Every Fluent articles need to be signed off by your respective feature crew and it needs to be a collective voice of the group. Once the group signs off, it will be reviewed by the reviewers who represents Fluent core, application, shell, etc. to ensure the guidance tells the story properly and provides sufficient steps that will help readers learn and apply the Fluent design system.

In order to kick this process off, authors need to send filled out [announcement template](#announcement-template) to [neondoc](mailto:neondoc@microsoft.com)

### The announcement template <a name="announcement-template">
When communicating with reviewers, please use [this template](https://microsoft.sharepoint.com/teams/osg_core_dep/UxP/Shared%20Documents/Forms/AllItems.aspx?FolderCTID=0x0120006CF971BD3F38B3418322FF2610FDA478&id=%2Fteams%2Fosg%5Fcore%5Fdep%2FUxP%2FShared%20Documents%2FWindowsStyleGuide%2FTemplates) to make the communication clear.

The intention of this template is to clearly communicate:
- Where the article you want reviewers to review is located (either link to a Word doc or link to review.docs.microsoft.com pointing to your draft page)
- What is this article supposed to communicate to audiences
- Who are the feature crews?

This announcement template will also be reviewed by the reviewers and the version that is 'signed off' is to be sent out as announcement at [later stage](#announcement).

### Article review process <a name="review-process">
Once the announcement template is sent to the reviewers, reviewers will provide feedback to both the announcement content itself as well as the article. Announcement content review will be done through e-mail. The article review will be done through the GitHub documentation authoring process.

## Sending the 'announcement' to **uwpcpnews** <a name="announcement">
Once the article is approved and your pull request has been pushed to appropriate branch, please take the announcement template you put together and reviewed with the reviewers in [step 4](publishing-and-announcing.md#announcement-template), make sure it is clean and pointing to the final documentation location you just published and send it to [UWPCPNews](mailto:UWPCPNews@microsoft.com).

## Don't forget to resolve the bug <a name="bug-resolve">
The process is tracked by the bug, so not resolving the bug results in you still showing up as owning an active topic. Be sure to resolve the bug and also be sure to add your final doc link to the body of the bug for tracking purposes.