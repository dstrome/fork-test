---
author: joshbax-msft
Description: Contribute to our private repository via local clone
title: Contribute to our private repository via local clone
ms.author: joshbax
ms.topic: article
ms.prod: windows
ms.technology: windows-oem
---
# Contribute to our private repository via local clone
You can also use git locally and clone the repo. This approach requires around 15-20 minutes of setup time, but it's way more efficient if you plan on creating or editing lots of content. It also lets you preview content locally.

This guidances makes some assumptions regarding basic Git knowledge. The instructions that follow can be executed in any environment that supports Git commands.

1. Clone the repository: 

    ```
    git clone https://cpubwin.visualstudio.com/commercialization/_git/commercialization`
    ```
2. In the root directory, create a new branch that'll hold your changes:

    ```
    git checkout -b my-branch-name
    ```
3. Push the new branch to origin. Note that all Microsoft employees should have CreateBranch permissions. You'll be an admin of this branch.

    ```
    git push -u origin my-branch-name
    ```
4. Make your edits. Note that while you're unrestricted in the changes that you can propose in this branch, for large-scale changes, be sure to stay in touch with the content owner.
5. Commit your changes, and push them to origin via some variant of the following:

    ```
    git add .
    git commit -m "descriptive message"
    git push
    ```
6. Go to the [Pull Requests](https://cpubwin.visualstudio.com/commercialization/_git/commercialization/pullrequests?_a=mine) page in our repository
7. Click the **New pull request** button
8. In the left dropdown, choose the branch you've created; choose **master** in the right dropdown if it isn't already selected
9. Review your changes, provide a meaningful description, and click **Create**
10. Though optional, it'd be a good idea to give the content owner a heads-up that you've requested a change. The owner will come along at some point, review your changes, and complete the pull request. After that, the content should publish within one business day.
