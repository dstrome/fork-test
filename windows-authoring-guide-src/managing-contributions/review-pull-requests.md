---
author: v-mikmat
title: Responding to customer contributions
---
# Responding to customer contributions -- Pull Requests

## Reviewing Pull Requests

Every workday morning, a CX administrator reviews PRs for each public repo. Simple fixes that require no technical evaluation are approved without further writer involvement. For PRs that require technical review, the admin assigns the request to the writer who owns the affected content.

### Expectations for review
Once assigned, a writer should take steps to accept and merge, approve with suggestions, or reject each PR. The writer communicates as necessary with the contributor. The writer has **5 business days** to resolve the pull request. Once approved, the PR will be merged in to the live content the following morning. 


Pull Requests may come from two places -- Internal PRs from the private VSTS repo, External/Public PRs from the GitHub repo. The admin will merge approved contributions to these public and private repos daily to keep them in sync. If the merged content builds safely, it is published from the private repo to the live site the following morning.

### How to approve a Pull Request
When a PR is assigned to you, you will receive an email containing a link to the PR on the repo. You have five business days from when you receive that message to resolve the PR. 

1. Click the link in the email (typically it's just the PR number) to go directly to the content repo.
2. In the **Conversation** tab, read what the contributor has said about the commit.
3. Select the **Files changed** tab to inspect the proposed changes directly. You can choose either a *source diff* or a *rich diff* view. You can also make additional changes to the affected files and commit them if you like.
4. If the PR currently bears the red label indicating that a content license agreement (CLA) is required, take no further action until the label says that the CLA has been signed. <!-- Need more info re: how the CLA mechanism works on GH. -->
5. Decide whether to [accept](#accepting-a-pr) or [reject](#rejecting-a-pr) the PR

### Accepting a PR
1. If you can accept the PR as it is, go right on to step 2. Otherwise, you can modify it by:
   a. Making changes to the affected files yourself and adding them to the pull request. Click the pencil icon to the right of the diff pane to edit the current file.
   b. Requesting that the contributor make changes. On the **Files changed** tab, select **Review changes** and then the **Request changes** option. Explain the changes you want in the **Review summary** box and then select **Submit review**. (*For documentation, it should not often be necessary to request that the contributor make changes.*)
   <br />When any necessary modifications to the PR are complete, continue with step 2.
2. Still on the **Files changed** tab, select **Review changes** and add a comment in the **Review summary** box. (Note that GitHub will notify the contributor of your approval in the next step, and whatever you write in the review summary will be included in that email message.) 
3. Select the **Approve** option, and then select **Submit review**. This returns you to to the **Conversation** tab and unblocks the PR for merging into the docs branch. 
4. Scroll down until you see the green **Merge pull request** box, click the drop-down arrow on the right side of it, and make sure that **Create a merge commit** is selected there.
5. Click **Merge pull request**. The button is replaced by a commit message and the **Confirm merge** button. 
6. Edit the commit message as appopriate (think about what the contributor may need to know about what you're doing), and then click **Confirm merge**.
7. The change is merged into the Master branch of the repo and will be published live within the next two business days.

### Rejecting a PR 

1. Select the **Conversation** tab and scroll down to the comment box at the end.
2. In the comment box (where you see the default text, "Leave a comment"), provide an appropriate explanation to the contributor for why the PR is being closed and not merged. 
3. Select **Close and comment**. The PR is closed, and the proposed changes are not merged into the GitHub repo.

### Important reminders

- **Get set up**&mdash;To handle pull requests for our public content, you must have a Microsoft-associated GithHub account and be a member of the MicrosoftDocs organization on GitHub. If you haven't done so already, follow the steps at [Set up a GitHub account](../github-account.md).
- **Communicate!**&mdash; Keep contributors informed as necessary, and remember to thank them for their input. For good guidelines, see the [Customer etiquette](https://review.docs.microsoft.com/en-us/help/contribute/contribute-how-to-manage-act-guidelines-public-pr#customer-etiquette) section in the docs.microsoft.com Contributor Guide.
- **Review carefully**&mdash;Test builds are not avaiable from our GitHub repos. Try to make sure that changes you approve are sound and unlikely to break our build after they are merged into our VSTS sources.

## See also
- [Guidelines for responding to public pull requests (OPS Contributor Guide by docs.microsoft.com)](https://review.docs.microsoft.com/en-us/help/contribute/contribute-how-to-manage-act-guidelines-public-pr)


*Still have questions? Contact a human at [Windows Open Publishing Support](mailto:winopsup).*