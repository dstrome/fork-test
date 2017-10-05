---
description: Set up a GitHub account.
title: Set up a GitHub account
---
# Setting up your GitHub account

## 1. Sign up for GitHub
To get a Microsoft associated GitHub ID, you need to create a GitHub account. To sign up, go to [https://github.com/join](https://github.com/join).

> [!NOTE]
> Take the following security precautions:
> - Create a [strong password for your Github account](https://github.com/settings/admin).
> - Enable [two-factor authentication](https://github.com/settings/two_factor_authentication/configure).
> - Save your [recovery codes](https://github.com/settings/auth/recovery-codes) in a safe place.

## 2. Connect your GitHub account and MS alias on the Microsoft Open Source portal
- Go to [https://repos.opensource.microsoft.com/](https://repos.opensource.microsoft.com/)
- Sign in to your GitHub Account
- Authorize the Microsoft Open Source Repo
- Click to link your accounts
- Join the **"Microsoft"** and **"MicrosoftDocs"** organizationsb

> [!NOTE]
> For more information about these Microsoft GitHub organizations and MS open source policies, see [How to Join the Microsoft Organization](https://www.1eswiki.com/wiki/How_to_Join_the_Microsoft_GitHub_Organization).

## 3. Update your public profile settings
Next, update your public profile settings so that readers can identify you with your topics:

1. Go to your repository at https://github.com/Microsoft/...
2. On the top right, select the drop-down arrow next to your profile photo, and then select **Settings**.
3. Set **Name** to **your first and last name** (this is what people will see on your live published pages on MSDN). This way Microsoft-internal users can contact you through the GAL.
4. Set **Public email** to **Don't show my email address**. This is so you won't get pinged by external-to-Microsoft readers.
5. You can also upload a **profile picture** (optional).

## 4. Set up Git Credential Manager for Windows
- Download and install [Git Credential Manager for Windows](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest). *You only need to set this up once, regardless of whether you plan to work in multiple different repos.*
> Note
> The download link is at the bottom of this linked page and will be named something like* `GCMW-*.*.*.exe`. This will also install Git if you don't already have it installed on your machine.

- Configuring Git -- If this is the first time you've installed Git on a new machine, you need to configure Git by giving it your name and email address. You can read more details [here](https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup).

`C:\Documents\VSTS\windows-uwp>git config --global user.name "Your Name"`

`C:\Documents\VSTS\windows-uwp>git config --global user.email youralias@microsoft.com`

- You don't need to do anything else to use Git Credential Manager. It magically works when credentials are needed. For example, when pushing to Visual Studio Team Services, it automatically opens a window and initializes an oauth2 flow to get your token.

## Learn more
Read more about everything you need to know for [initial authoring set up on the Docs/OPS Guide](https://review.docs.microsoft.com/en-us/help/contribute/contribute-get-started-initial-setup).

- [What is GitHub?](https://guides.github.com/activities/hello-world/#what)
- [Understanding Git](/writing-guidance/understanding-git.md)
- [Git and GitHub essentials](https://review.docs.microsoft.com/en-us/help/contribute/contribute-get-started-git-github-fundamentals)
- [What is Markdown?](https://guides.github.com/features/mastering-markdown/#what)
- [Resources for writing markdown](/writing-guidance/writing-markdown.md)
- [How to set up a Livefyre Account for responding to comments](/managing-contributions/respond-to-comments.md)
- [Docs Help Documentation: Onboarding Guide, Contributing Guide, Style Guide](https://review.docs.microsoft.com/en-us/help/)
- [Submit or vote for site suggestions on the Docs.microsoft.com User Voice site](https://msdocs.uservoice.com/forums/364242-general-site-feedback)