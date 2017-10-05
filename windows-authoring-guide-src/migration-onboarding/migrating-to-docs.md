---
author: tedhudek
---

# Migrating to docs.microsoft.com

This page describes the steps necessary to move existing OPS content from MSDN/TechNet to Docs.microsoft.com.

If you'd like to see implementation examples as you read, please visit the live branch of <https://cpubwin.visualstudio.com/drivers/_git/drivers>.

This repo publishes to https://docs.microsoft.com/windows-hardware/drivers.

Before you get started, contact Paulina Cortes in APEX, and get on her migration schedule.  She will send you a tick tock that lists the migration steps.

## Review table of contents

Docs officially supports a maximum of six header levels (######) in any TOC.md, and recommends no more than four (####).

If you have more than six, nothing breaks, but your TOC pane on the left side will have some very narrow and hard-to-read titles.

If your repo has more than one thousand topics, consider at least two levels of TOCs, meaning one root TOC.md that references directories, each of which has its own TOC.md.  This will make it easier to reduce the number of heading levels.

## Create a staged copy of your content

In this step, you'll set up a new repo and get your content test staged on Docs.  Here's how:

1. Create an empty repo. ("myrepo-test"), i.e. https://cpubwin.visualstudio.com/drivers/_git/myrepo-test
2. Clone it to local.
3. In empty clone, add remote (we'll call the remote "existing" here) to existing content repo, fetch refs.
4. Merge existing/master into new clone's master.
5. Push content up to new empty test repo.
6. Use http://ops to get your new test repo publishing to <https://review.docs.microsoft.com>.

## Add PDF button to rendered pages

See the `.openpublishing.publish.config.json` file in <https://cpubwin.visualstudio.com/drivers/_git/drivers> (live branch).

It's the version of the json in the live branch that determines which branch gets the button.

You need to set `"need_generate_pdf_url_template": true` to get the button on rendered content out of all branches.
Then for each branch that should have a PDF built for it, add that branch to this section:

```
 "branch_target_mapping": {
   "live": [
       "Publish",
       "Pdf"
   ]
   ```

Note that branches that build PDFs take a long time, so likely just the live branch here.

If you run into trouble, ask Ted Hudek, or send mail to <dendeli@microsoft.com>.  He wrote the PDF code.

## Add universal header footer (UHF)

You might need to create a universal header footer for your content on Docs.

Here are the basic steps:

1. Set up a Category Menu, publish it and then send Rob Eisenberg the Compass location.  If you have no idea how to do this, ask Janet Thomas or Kelly Pittman.
2. Rob will send back a uhfHeaderId to add to your docfx.json file.
3. With that in place, you’ll begin to see your header show up.

See Rob's walkthrough here: <https://opsdocs.azurewebsites.net/en-us/opsdocs/partnerdocs/customizing-the-uhf?branch=master>.

## Update breadcrumbs

You'll need to make a few updates so that your breadcrumbs go all the way up to the Docs root node.

Examine the `TOC.yml` file in <https://cpubwin.visualstudio.com/drivers/_git/drivers>.  Be sure to update the base path (first part of the URL), as well as configure the top few nodes to go to the destinations you want.

Add a line like this to your docfx.json:

` "breadcrumb_path": "/windows-hardware/drivers/breadcrumbs/toc.json"`

And:

` "files": ["**/**.md", "**/**.yml"],`


## Configure LiveFyre

If you want to use the LiveFyre system for managing customer comments, you'll need to configure it.

For details, see [Respond to comments](../managing-contributions/respond-to-comments.md).

## Redirection

Determine if you need topic level or site level redirection.  Topic level means you are reconfiguring the directory hierarchy.  In this case, redirecting requires a full topic to topic mapping in a CSV file.

Site level means you are just changing the front part of the URL, but directory hierarchy and filenames remain the same.  This is much easier.  Request site level in the GoLive ticket and Sandra will open a task to create an AAR rule.

Here is a sample bug for a site level redirect: https://mseng.visualstudio.com/DefaultCollection/VSChina/_workitems?_a=edit&id=886203

To open a topic level redirection request, use https://msdnhelp.corp.microsoft.com/NewRequest.aspx?formid=9.

Update your repo's redirection json to match the new URL base path.

## Verify customized 404 page

If you had a customized 404 page before migrating, verify that it appears correctly on Docs.  Note that the link target to your 404 image in `404.md` should be an absolute link in the form `/windows-hardware/drivers/images/fish.png`.  In MSDN/TechNet OPS, a relative link was fine here but in Docs it must be an absolute link.

Alternatively, you can embed the image source into the `404.md` file, as described in http://stackoverflow.com/questions/8499633/how-to-display-base64-images-in-html.

## Update GitHub blurb

If you have a GitHub repo, update the rendering URL destination in the top-level blurb, and your README.md and/or CONTRIBUTING.md, as applicable.

## Get clean CATS test pass for P0 issues

When you create a new run in http://contentqa_cats/, the pre-checked items on screen 2 ("Select Test Cases") are the P0 ones.

CATS required metadata is: ms.author, ms.date, ms.topic, and either ms.service or ms.prod.  Here's what we added:

```
ms.author: windows-driver-content
ms.date: 04/04/2017
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-devices
```

The last two values came from Gilda, who verified them with the SkyEye team.

The tools in https://osgcpubdev.visualstudio.com/DefaultCollection/_git/WdcUtils are very helpful for automating metadata passes.  Contact Michael Satran or Alex Koren.  Note that you may run into line ending issues, which Ted Hudek has a script to fix.

## Get ok from WDG BI folks, clear for P0 issues

Work with Tracey and Gilda to get an SEO review of your content.  You'll get a spreadsheet with different tabs containing recommendations, such a max/min title length, description length, etc.

For max YAML title length, it's 95 minus stuff that Docs bolts on, which is by default ` | Microsoft Docs`.  Some teams, like UWP, add a suffix in docfx.json:

`        "titleSuffix": "UWP app developer"`

If you do this, you should also subtract that string from the 95, so in the end you might only have 65 chars or so.  You can see what HTML title is by mousing over a tab title in the browser.

## Coordinate with Localization

If your content is localized, contact Eliza Tobias and let her know your migration date.

## Resources

- [Docs Onboarding Process](https://review.docs.microsoft.com/en-us/help/onboard/onboarding-process-overview)
- [Onboarding to Open Publishing and docs.microsoft.com](https://opsdocs.azurewebsites.net/en-us/opsdocs/onboarding-steps?branch=master)
