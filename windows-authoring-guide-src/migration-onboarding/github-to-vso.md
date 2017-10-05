---
author: tedhudek
---

# Move a repo from GitHub to Visual Studio Online

> [!IMPORTANT] 
> These guidelines are for administrators only; if you are a writer, contact your administrator.

This is the general workflow for migrating from one server-based repo to another. You can also use this general workflow to set up a public repo that mirrors some subset of the content in your private repo.  

## Creating a new repo in Visual Studio Online (VSO)

1. Create your new repo in https://cpubwin.visualstudio.com/_git/. If you have problems with permissions, email `wdgopscrum`.
2. Clone the empty VSO repo: `git clone https://cpubwin.visualstudio.com/_git/newrepo`, and then enter `cd newrepo`.
3. Add a remote pointer to your old GitHub repo: `git remote add gh https://github.com/Microsoft/MyRepo.git`
4. Use the following pair of commands to copy the master branch from GitHub to VSO:
    ```
    git pull gh master
    git push origin master
    ```
  Repeat this step for each branch that you want to copy.

5. On GitHub, modify the repo's intro text below the top level tabs to point to the new repo.
6. Notify Sandra Aldana Abad that you are ready to switch Open Publishing from the GitHub repo to VSO. She will create a new docset for you and make other necessary changes in the OP portal. She will then update the `/.openpublishing.publish.config.json` file in your VSO repo to point to the new docset.
7. After you have verified that your content is publishing successfully and you have migrated all the branches that you need, it's a good idea to delete the old GitHub private repo. To do this, you must have admin privileges. 
   
    1. In GitHub, select the **Settings** tab.
    2. Scroll to the bottom of the page, and select the **Delete this repository** button.

## Enabling public contributions

While you don't have to enable public contributions when you migrate to VSO, some teams like to do this at the same time as the VSO migration. For that reason, we include the steps here:

1. Create your new public repo.
2. Turn on automated handling of CLAs (Contribution License Agreements): 

    1. Configure a dedicated DL with external senders enabled.
    2. Turn on CLA automation at https://opensourcehub.microsoft.com/. If you have problems, email *cla-automation*.
    
3. In your openpublishing.publish.config.json file, add: 
    
    ```
    "open_to_public_contributors": "true", 
    
    "git_repository_url_open_to_public_contributors": "https://github.com/Microsoft/windows-driver-docs",  
    "git_repository_branch_open_to_public_contributors": "master"  
    ```

## Adding a confidential branch

Typically, our VSO content repos have read permissions for WDG only. If you need to work on prerelease content that needs to be locked down even further, follow this procedure:

1. Create a new branch, either locally (`git checkout -b <branch name>`; `git push -u origin <branch name>`), or on the web (**Branches** tab > **New branch**). 
2. By default, the new branch inherits the same permissions as the branch you based it on. However, VSO allows you to set per-branch permissions.
3. On the **Branches** tab of VSO, find your new branch, click the `...` next to it, and then select **Branch security**.
4. Set the permissions as desired. You can add email DLs or individual names from the GAL to customize as needed. For example, you might have only your PM in the perms list. If you give your PM contribute perms on this branch, you can both collaborate right in the branch instead of the typical model where the feature team member has to create their own branch to contribute.

> [!NOTE]
> Content in your new branch is still staged when you commit, where it is visible to all FTEs. The permissions in the repo only apply to the repo itself.

## Syncing between public and private

You'll need to pick one branch that you will keep in sync between public and private. Typically, this is `master`, so that's what we'll use here. These directions assume that your remotes are named `vso` and `gh`.

In your local clone, use the following steps:

```syntax
# first, switch into the master branch
git checkout master

# fetch all remotes and merge into the current branch

git pull vso master
git pull gh master

# do a local merge if needed

git push vso master
git push gh master
```

Ensure that the server builds your changes cleanly, and then merge master into live and push to your publishing repo. 

