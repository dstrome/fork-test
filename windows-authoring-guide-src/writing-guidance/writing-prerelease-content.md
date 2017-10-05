---
author: misaso
description: windows resources for working with pre-release content
title: Working with pre-release content
ms.author: misaso
ms.topic: article
ms.prod: windows
---

# Working with pre-release content

Pre-release or tented content is content that is not yet publicly available. Oftentimes, writers work with pre-release content in order to ship simultaneously with the feature or product. The process is similar to writing new content, except that the content must remain hidden until it is ready to be published. When working with pre-release or tented content, it's important that you keep the content in an internal repository like VSTS, until you are ready to publish.

> [!IMPORTANT]
> Do not work with pre-release or tented content in GitHub repositories, even though private repositories are available.

## Use an existing VSTS repo

If your team already has a VSTS repo set up for documentation, and your new content is not tented, the process is simple. You can find the VSTS repo for your content by visiting the review.microsoft.com staging site for your content and clicking the "Edit" button, then complete the following steps. 

1. Clone your team's repo.

    `git clone https://cpubwin.visualstudio.com/_git/<repo_name>`

2. Create your own branch from the master branch of your team's repo to start working. See [Adding a confidential branch](https://review.docs.microsoft.com/en-us/windows-authoring-guide/migration-onboarding/github-to-vso#adding-a-confidential-branch) for information on how to set permissions.

    `git checkout -b <your new branch name>`

3. Once you've committed the new content, push your branch to the remote repo for review on a staging server. You will get an email from OPS (Open Publishing Build Service) with a link to the preview.

    > [!Note]
    > The staging server is visible to anyone at Microsoft. If your pre-release content should not be visible to employees at Microsoft, do not use a VSTS repo that has already been published.

4. Submit the content to your reviewers.

    > [!TIP]
    > Send the staging URL to your reviewers, and allow them to make changes to your branch by clicking the Edit button and creating a Pull Request.

When your content is ready to be published, merge your branch into the appropriate branch for release (ie. Master for current release, RS3, etc).

## Create a private VSTS repo

If your team does not already have a VSTS repo set up for documentation, or you do not want your topic to be published to a staging server, follow these steps to set up a private repo.

1. Go to http://www.visualstudio.com and sign in with your org (user@microsoft.com) email. Go to your profile page.

2. Click **Create new account** to create a new VSO account.

    ![Create new account](images\create_new_account.png)

3. Name the account something you'll remember, like *\<pre-release-project-hush-tented\>*. Then choose **Git** under **Manage code using:**, and click **Continue**.

    This creates a new account and project at:

     `https://<account-name>.visualstudio.com`

     You can use the default project, **MyFirstProject**, or create a new project, to start working. Note that when you create a new project, remember to choose **Team Members** under **Share with**, to keep your project private.

4. To allow other users to view or contribute to your project, open the Settings menu, and on the left pane under **Teams**, choose **\<project-name\> Team** and on the right pane, choose **Members**. Click **Add** to add members.

    > [!IMPORTANT]
    > By default, you will be listed in the **Project Administrators** group for your account and project. You can add users to the **Project Administrators** group, but it is important that you do not remove yourself.

    For more information about working with Visual Studio account permissions, see [Manage users and access in VSTS](https://docs.microsoft.com/en-us/vsts/accounts/add-account-users-assign-access-levels).

To delete a project:

1. Go to the admin page of the account:

    `https://<account-name>.visualstudio.com/_admin`

    And open the **Settings** menu.

2. Next to the project name, click the ellipses (...) and choose **Delete**.

When you are finished with the account, you might want to delete the account for clean up purposes. To delete the account, open the **Settings** menu, and under **Account | Advanced administration tasks**, click **Delete Account**.

For more information about working in Visual Studio online, see [Account Management](https://docs.microsoft.com/en-us/vsts/accounts/index).

## Keeping your private VSTS repo and public GitHub repo in sync

*Steps coming soon.*