---
author: mikematteson
---

# Pull-request monitoring (public GitHub repos)


<hr />
<span style="font-family: stencil,arial,verdana;font-size:18pt;color:darkred;opacity:0.4">DRAFT</span>&nbsp;&mdash;&nbsp;<span style="font-weight:bold; color:darkred">This content is not yet ready for use.</span>
<hr />


*Last updated: May 17, 2017*

- **Platform:** docs.microsoft.com
- **Repos:** windows-uwp, winrt-api, winrt-related
- **Team:** WDG CX Developer
- **Frequency:** Daily (triage of new PRs); Weekly (stale request follow-up)

> [!IMPORTANT]
> These instructions are exclusively for those responsible for administering the GitHub pull-request workflow. **If this function isn't part of your regular duties, don't perform the procedures described here.** 

These instructions are for daily triage and weekly follow-up of public pull requests (PRs) submitted via GitHub regarding public content on the listed repos.

## URLs of PR lists

Here are the URLs of the PR lists for each public repo.

<table>
<tr><th>GitHub repo</th><th>PR list URL</th></tr>
<tr><td>windows-uwp</td><td>https://github.com/MicrosoftDocs/windows-uwp/pulls</td></tr>
<tr><td>winrt-api</td><td>https://github.com/MicrosoftDocs/winrt-api/pulls</td></tr>
<tr><td>winrt-related</td><td>https://github.com/MicrosoftDocs/winrt-related/pulls</td></tr>
</table>

## Triage of new PRs (daily)

Follow these steps to evaluate and assign new PRs for [each public repo](#urls-of-pr-lists).

**For each GitHub repo:**

1. Go to the PR list for the repo. (Find the URL in the table at [URLs of PR lists](#urls-of-pr-lists).)
2. If there are no unassigned PRs, triage of this repo is complete. Move on to the next repo and restart the triage process.
3. If new (unassigned) PRs do appear in the list, for each new PR:

   a. Select the PR title to open the unassigned item.

   b. Select the **Files changed** tab and review the changes submitted with the PR. If the changes are trivial and require no application of technical judgement, you may choose to approve and merge them yourself; see [Accepting a PR](../managing-contributions/review-pull-requests.md#accepting-a-pr). Otherwise, continue here.

   c. Determine the owner of the affected file or files.

      - **windows-uwp**, **winrt-related**: Select the **View** button and look in the topic metadata for the author/owner's alias.

      - **winrt-api**: Determine the namespace from the file path shown in the GitHub UI, and then find the owner:

         - WinRt_Namespace_Owners_*.xlsx on [SharePoint](https://microsoft.sharepoint.com/teams/osg_core_dcp/cpub/dev/Shared%20Documents/Forms/AllItems.aspx?RootFolder=%2Fteams%2Fosg%5Fcore%5Fdcp%2Fcpub%2Fdev%2FShared%20Documents%2FRelease%20Management%2FResources&FolderCTID=0x012000C025F0C3AF19534FA8E738B5AEE4BBC7&View=%7B2F871040%2D000C%2D4A76%2DB6E3%2DECE6C2D351E9%7D).
         
         - If the namespace is not listed in the spreadsheet, inspect the Git log of the file for clues about who's been working on it the most; typically that'll be either the content owner or somebody who knows who the owner is. 


   d. Assign the PR to the owner:

      1. Return to the PR list page and select the check box to the left of the item you're about to assign.

      2. Select **Assign** to see the **Assign someone** drop-down list of eligible assignees.

      3. Find the content owner in the list and click the name to assign the PR to that person. 
      
     > [!NOTE]
     > Some folks have rather obscure GitHub aliases. If you can't find someone, try looking it up by their Microsoft alias in the [Table of GitHub aliases](#finding-content-owners).)

   e. Apply the [PR checklist](https://review.docs.microsoft.com/en-us/windows-authoring-guide/managing-contributions/editorial-checklist?branch=master) as appropriate. [TODO: Add more detail here.]

## Follow-up on stale PRs (weekly)

A PR is stale if the GitHub pull-request summary page identifies it as 7 days old or older. Follow these steps to identify and report stale PRs for [each public repo](#urls-of-pr-lists).

1. In your email client, start an email based on the stale-PR report template.

2. Open the Pull Request UI in the first repo (probably windows-uwp).

3. Use the Windows Snipping Tool to take a partial screenshot of the area of the Pull Request UI that shows the active PRs and the owners assigned to them.

4. Paste the image into the email message under the appropriate label for the repo. (If you're in Outlook, visual clarity, you can add a solid border and modest drop shadow to the screenshot.)

5. Repeat steps 2-4 for the remaining repos (probably winrt-api and winrt-related)

6. Adjust the text at the beginning of the email to match the state of the PRs: how many there are, how many are stale. Also adjust the due date of the call to action (typically the coming Friday, if the report is sent near the beginning of a week).

7. Add the assignees of the stale PRs to the To: line.

8. On the Cc: line, add the assignees of any non-stale PRs, plus MartinDirs, JasGro, v-MikMat, and v-KBaker.

9. Send the email.

## Finding content owners

### Table of GitHub aliases

<table>
<tr><th>MSFT</th><th>GitHub</th></tr>
<tr><td>aablackm</td><td>aablackm</td></tr>
<tr><td>abigailc</td><td>abbycar</td></tr>
<tr><td>alkoren</td><td>awkoren</td></tr>
<tr><td>brendm</td><td>bmitchell287</td></tr>
<tr><td>drewbat</td><td>drewbatgit</td></tr>
<tr><td>elcowle</td><td>eliotcowley</td></tr>
<tr><td>edoyle</td><td>erikadoyle</td></tr>
<tr><td>jenhayes</td><td>JnHs</td></tr>
<tr><td>jillfra</td><td>jillfrank</td></tr>
<tr><td>jimwalk</td><td>jwmsft</td></tr>
<tr><td>joanlee</td><td>joannaleecy</td></tr>
<tr><td>jken</td><td>GrantMeStrength</td></tr>
<tr><td>johnshaw</td><td>shawjohn</td></tr>
<tr><td>joshuapa</td><td>JoshuaPartlow</td></tr>
<tr><td>kbridge</td><td>Karl-Bridge-Microsoft</td></tr>
<tr><td>karler</td><td>KarlErickson</td></tr>
<tr><td>kellypi</td><td></td></tr>
<tr><td>kevinasg</td><td>KevinAsgari</td></tr>
<tr><td>lahugh</td><td>laurenhughes</td></tr>
<tr><td>libbymc</td><td>libbymc</td></tr>
<tr><td>mhopkins</td><td>Xansky</td></tr>
<tr><td>markl</td><td>mcleblanc</td></tr>
<tr><td>martinek</td><td>martinekuan</td></tr>
<tr><td>mattwoj</td><td>mattwojo</td></tr>
<tr><td>mcleans</td><td>mcleanbyron</td></tr>
<tr><td>misatran</td><td>msatranjr</td></tr>
<tr><td>mstahl</td><td>M-Stahl</td></tr>
<tr><td>mithom</td><td>michaelfromredmond</td></tr>
<tr><td>mijacobs</td><td>mijacobs</td></tr>
<tr><td>mtoepke</td><td>mtoepke</td></tr>
<tr><td>mukin</td><td>muhsinking</td></tr>
<tr><td>normesta</td><td>normesta</td></tr>
<tr><td>pafarley</td><td>PatrickFarley</td></tr>
<tr><td>quradic</td><td>QuinnRadich</td></tr>
<tr><td>rosshe</td><td></td></tr>
<tr><td>ryanth</td><td>ryanthmaf</td></tr>
<tr><td>scotmi</td><td>sdgmiller</td></tr>
<tr><td>susanw</td><td>athousandwords</td></tr>
<tr><td>twhitney</td><td>TylerMSFT</td></tr>
<tr><td>v-mikmat</td><td>mikematteson</td></tr>
<tr><td>v-angraf</td><td>v-angraf</td></tr>
<tr><td>v-doklop</td><td></td></tr>
<tr><td>v-ginai</td><td></td></tr>
<tr><td>v-kbaker</td><td>Kellylorenebaker</td></tr>
<tr><td>v-kevsch</td><td>kevin-schultz</td></tr>
<tr><td>v-nickos</td><td>v-nickos</td></tr>
<tr><td>v-rbrand</td><td></td></tr>
</table>

