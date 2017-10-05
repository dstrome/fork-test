---
author: glitterprincess
---

# Guidance for moving from GitHub to Visual Studio Team Services

**In this topic**:
- [Overview](#overview)
- [Action items (quick version)](#action-items-quick-version)
- [Action items (comprehensive version)](#action-items-comprehensive-version)

## Overview
### What's happening?
We've changed the back-end repo location for the windows-apps repo, moving it from GitHub over to Visual Studio Team Services (VSTS).  
- New VSTS repo: [https://cpubwin.visualstudio.com/windows-uwp/_git/windows-uwp](https://cpubwin.visualstudio.com/windows-uwp/_git/windows-uwp)
- We've modified the repo name to “windows-uwp” for better OP alignment.
- All of Martin Ekuan's org (FTE and non-FTE) has Write perms, and all of the Windows Devices Group has Read and pull request perms. 
- You will continue to use markdown, but will sync it to the VSTS system instead of GitHub.

Moving the repo back-end to VSTS will allow us to maintain security of pre-released content while at the same time open up the benefits of public contributions. 

### How is this going to look?
We've migrated the content from our current GitHub repo (windows-apps) over to the VSTS repo (windows-uwp), and hooked up the OP pipeline to the new VSTS repo.

At a later time we will connect the VSTS repo to a new GitHub (Public) repo to enable public contributions to the content.

### Will branches work the same way?
This migration will move all branches into VSTS, which will be kept in sync with the VSTS repo master branch each day at publish time.

Branch management of master, live, and rs2 will still be the responsibility of the managed service in this new architecture&mdash;and writers will be responsible for the management of their personal branches.

### Is there a tool change to support this new architecture?
Everything you wrote in markdown and uploaded to GitHub will be migrated over and should work just the same; this is a back-end migration only. After the migration takes place, writers will need to verify this migration by clicking through their content. The tool we formerly recommended to keep your local clone in sync with GitHub was GitHub Desktop for Windows; however, this tool will no longer work in VSTS, so we are recommending migrating to Visual Studio for VSTS management.

### How will our partner teams and externals contribute?
**Partner teams** should use VSTS to create their pull requests for changes to content. 

**Developers who are external to Microsoft** will be able to use the **Contribute** button on the live page after we create the public GitHub repo. This button will redirect the user to the GitHub public repo where they can suggest changes via a pull request. 

At publish time each day, writers will review the requests in the GitHub public repo and determine how best to handle them&mdash;if accepted they will integrate the change into the VSTS repo.

## Action items (quick version)
We are moving from GitHub to VSTS for security reasons. Run the following commands and you will be able to continue your work in VSTS. If you have any questions or concerns, please contact [WDG OP Scrum](mailto:wdgopscrum).

> [!NOTE]
> If you are asked for sign-in credentials, you'll need to create a Personal Access Token in Visual Studio to allow the command line to access the repo. You can find full instructions at [Work from the Git command prompt](https://www.visualstudio.com/en-us/docs/git/command-prompt#create-a-personal-access-token-for-your-visual-studio-team-services-account).

1. To see your current email, run `git config --global user.email`.
2. If your email is not set to your Microsoft domain email, run the following command, replacing `<email>` with your work email:

  `git config --global user.email "<email>"`

3. Verify that the origin remote is set to GitHub: `git remote -v`; you should get the following output:

  ```
  origin  https://github.com/Microsoft/windows-apps.git (fetch)
  origin  https://github.com/Microsoft/windows-apps.git (push)
  ```

4. Enter the following command: 
  
  `git remote set-url origin https://cpubwin.visualstudio.com/windows-uwp/_git/windows-uwp`
  
5. Verify that this change was successful: `git remote -v`; you should get the following output:

  ```
  origin  https://cpubwin.visualstudio.com/windows-uwp/_git/windows-uwp (fetch)
  origin  https://cpubwin.visualstudio.com/windows-uwp/_git/windows-uwp (push)
  ```

## Action items (comprehensive version)

For writers who are currently using GitHub for their work, they will need to migrate to use VSTS as their primary remote repo source. This means they will need to reset their tools that are currently pointed at GitHub to point to VSTS.

There are two ways to edit content:

1.	**Web browser** – As the systems change, you will still be able to point users to the VSTS page to make quick updates and commit directly into the repo. It may look a bit different from GitHub, but this functionality is still available.
2.	**Local copy** – Most writers are cloning a copy to their local system, and then syncing back with the remote repo. 

When GitHub was originally introduced to CPub, the golden path for tools was to use GitHub Desktop for Windows and Visual Studio Code mainly because these tools were lightweight and supported by their respective companies. GitHub Desktop for Windows, as an example, provided an easy method to learn about cloning and keeping content in sync&mdash;unfortunately, it will not work as we transition the repo to VSTS, so you will need to adopt new tools.

As we look at the options for new tools, following are the potential scenarios (with guidance) in which you may find yourself:

- **You are currently using GitHub Desktop for Windows** – If this is your primary tool for sync’ing your content, you will need to change to a new tool set.
  - If comfortable with using the command line, please change to posh-git (PowerShell-based git tool).
  - If not comfortable with the command line, please change to Visual Studio 2015.
- **You are currently using git-bash or posh-git** – If you are already at the command line, your path to migration is quite simple: register to the new remote server for VSTS and you are all set.

Based on the scenarios outlined above, you will need to take one of the following actions:
- [Change your remote from GitHub to VSTS and set your email](#change-your-remote-from-github-to-vsts-and-set-your-email)
- [Change from GitHub Desktop for Windows to posh-git (and VSTS)](#change-from-github-desktop-for-windows-to-posh-git-and-vsts)
- [Change from GitHub Desktop for Windows to Visual Studio 2015 (and VSTS)](#change-from-github-desktop-for-windows-to-visual-studio-2015-and-vsts) 

### Change your remote from GitHub to VSTS and set your email
If you are already using posh-git to keep your local clone in sync with GitHub, you will only need to change the remote server&mdash;from GitHub to VSTS.  

> [!NOTE]
> If you are asked for sign-in credentials, you'll need to create a Personal Access Token in Visual Studio to allow the command line to access the repo. You can find full instructions at [Work from the Git command prompt](https://www.visualstudio.com/en-us/docs/git/command-prompt#create-a-personal-access-token-for-your-visual-studio-team-services-account).

**To change your email**:

1. To see your current email, in any command-line window, run `git config --global user.email`.
2. If your email is not set to your Microsoft domain email, run the following command, replacing `<email>` with your work email:

  `git config --global user.email "<email>"`

**To change your remote**:
 
1. Open a posh-git window.
2. Verify that the origin remote is set to GitHub: `git remote -v`; you should get the following output:

  ```
  origin  https://github.com/Microsoft/windows-apps.git (fetch)
  origin  https://github.com/Microsoft/windows-apps.git (push)
  ```

3. Enter the following command: 

  `git remote set-url origin https://cpubwin.visualstudio.com/windows-uwp/_git/windows-uwp`

4. Verify that this change was successful: `git remote -v`; you should get the following output:

  ```
  origin  https://cpubwin.visualstudio.com/windows-uwp/_git/windows-uwp (fetch)
  origin  https://cpubwin.visualstudio.com/windows-uwp/_git/windows-uwp (push)
  ```

The results of your request should indicate the new remote origin server, and if so, you are all set to begin working just as you had done in the past, only now you will pull and push to the VSTS.

### Change from GitHub Desktop for Windows to posh-git (and VSTS)
If you are ready to make the migration from the GitHub Desktop for Windows gui-based system to a command-line option, this would be a good time to make the transition. Although you are welcome to use whichever tool you like for sync’ing with the repo, we will support a golden path that utilizes posh-git, the PowerShell implementation of git.  

- **[posh-git](https://github.com/dahlbyk/posh-git/blob/master/readme.md)** - A PowerShell module which provides Git/PowerShell integration. Posh-git is a command-line tool that runs in a PowerShell prompt. It utilizes the same commands as git-bash, but also affords the extended functionality of PowerShell.
  
**To install posh-git**:

1. Open a PowerShell window.
2. Execute the following command:
  
    `(new-object Net.WebClient).DownloadString("http://psget.net/GetPsGet.ps1") | iex`
3. Clone the new repo to your system:
    
  `git clone https://cpubwin.visualstudio.com/windows-uwp/_git/windows-uwp`

> [!NOTE]
> If you are asked for sign-in credentials, you'll need to create a Personal Access Token in Visual Studio to allow the command line to access the repo. You can find full instructions at [Work from the Git command prompt](https://www.visualstudio.com/en-us/docs/git/command-prompt#create-a-personal-access-token-for-your-visual-studio-team-services-account).

After you have completed the download process as part of cloning, you are ready to go to work with your new clone connected to VSTS. For more information, see the [posh-git readme](https://github.com/dahlbyk/posh-git/blob/master/readme.md). 

### Change from GitHub Desktop for Windows to Visual Studio 2015 (and VSTS)
There have been several improvements of late to Visual Studio in the way it interacts with a git repository. As such, it is a viable alternative to working with posh-git.

- **Visual Studio** - The [Markdown Mode](https://visualstudiogallery.msdn.microsoft.com/0855e23e-4c4c-4c82-8b39-24ab5c5a7f79) plug-in provides real-time preview. The [Web Essentials](http://vswebessentials.com/) plug-in/extension provides a preview and syntax highlighting for .md files in Visual Studio 2015. These integrate well with GitHub repos as well as Visual Studio Online.
