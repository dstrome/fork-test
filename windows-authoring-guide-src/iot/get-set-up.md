---
author: mattwoj
description: Get set up for authoring Windows IoT docs 
title: Windows IoT docs authoring set up
ms.author: mattwoj
ms.topic: article
ms.prod: windows
ms.technology: windows
---

# Get set up for contributing to Windows IoT documentation 

Follow these instructions to configure your PC. It takes up to 20 minutes.

In order to contribute, you must first install Git on your machine:

### Installing Git 

The easiest way to get all the Git tools is to download [GitHub Desktop](https://desktop.github.com/).  This will install Git, Git shell, GitHub Desktop, and keep you up to date.

### Setting up Jekyll on Windows
1. Follow the [Jekyll on Windows](http://jekyllrb.com/docs/windows/) guide. 
2. Install Rouge
  
  `gem install rouge --no-ri`

### Fork the repository

1. Create a [GitHub](https://github.com/) account 
2. From GitHub Home, navigate to the repository you'd like to contribute to (e.g. ms-iot/content)
3. Click *Fork* 
4. Clone the repository in one of several ways: 
  1. Command line 
  
    `git clone [link to forked .git] [NameYourLocalFolder] `
  2. Launch the GitHub app 
  
     Click 'Clone or Download'
     

  3. Clone using the GitHub Desktop application. 
  4. Using your own git flow (e.g. sourcetree) 
 

For clarification:

**local repository:**: the cloned repository that you have one on your machine 

**forked repository:**: the fork you made from the main repository. This sits up on GitHub's servers. (Also known as "*origin*") 

**main repository:** the original repository that you forked from. This is the common ms-iot repository hosted on GitHub's servers. (Also known as "*upstream*") 


## For managing your Git Credentials we also recommend the following:

1. Download and install [Git Credential Manager for Windows](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest). The download link is at the bottom of the page and will be named similar to `GCMW-*.*.*.exe`. This will also install Git if you don't already have it
2. Open the **Git CMD** app from Start
    1. `mkdir C:\GitRepos\`
    2. `cd C:\GitRepos\`
    3. `git clone https://github.com/MicrosoftDocs/edge-developer.git`
    	This will create a local clone of the repo on your machine where you can do your authoring and then push back to the remote repo.
   
