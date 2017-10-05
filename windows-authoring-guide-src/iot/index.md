---
author: mattwojo
description: Contribute to Windows IoT docs. 
title: Authoring Windows IoT docs
ms.author: mattwoj
ms.topic: article
ms.prod: windows
ms.technology: windows
---

# Writing Windows IoT docs

Thank you for your interest in contributing to the Windows IoT Developer documentation. Windows IoT site pages and documentation is located in the **ms-iot/content repo**: [https://github.com/ms-iot/content](https://github.com/ms-iot/content).

## Where can I view content?
- [Windows IoT staging site](https://developer.microsoft-int.com/en-us/windows/iot?setvar=fltpreview:1) 
*(You can change which repo branch you are viewing in this staging environment as well.)*
- [Windows IoT live site](https://developer.microsoft.com/en-us/windows/iot)

To contribute:
- [Get set up](/get-set-up.md)
- [Making changes](#making-changes) 
- [Best practices for authoring](#best-practices)  

## Guidelines for authoring

When creating a new topic, or updating an existing one, there are a handful of things to keep in mind.

1. **Creating a new topic:**

  When creating new content, please start with the following templates (view in *Raw* mode):

  * [Sample template](https://github.com/ms-iot/content/blob/develop/Resources/contribute/template/sample-template.md)
  * [Documentation template](https://github.com/ms-iot/content/blob/develop/Resources/contribute/template/docs-template.md)
  
  **Be sure to add** your file to the correct index file:
  
  * Samples add to [_samples.json](https://github.com/ms-iot/content/blob/develop/_data/_samples.json)
  * Docs add to [_docs-index.json](https://github.com/ms-iot/content/blob/develop/_data/_docs-index.json)

2. **Save your files in the following directories**

  * Images: `content/Resources/images/<folder name>/<your filename>`
  * Documentation: `content/en-US/Docs`
  * Samples: `content/en-US/Samples`

**File naming rules**
  - Use upper camel case (e.g. BackgroundColor) when naming your files. Don't use hyphens or underscores in file names.
  - Use descriptive keywords that add context, relevance, and are human readable.
  - Do not use a trailing slash or special characters or spaces.
  - Do not use more than 80 characters - this is a publishing system limit.

**Changing file names, moving files, and redirects**
If you need to change a file name, be sure to:
- Change the .md file name and permalink. The filename and permalink should always match.
- Update the TOC.
- Update any links to the changed page. Be sure to search the entire repo for references to the old page location that need to be updated.
- When moving a file: Leave the existing file in it's old location, with the original permalink. Change the layout to "redirect" and delete all content under the metadata (section contained between ---) and place the following code in:
  `{% include redirect.html url="/windows/iot/<newURL>" %}`
This will create a client side redirect to the new page for any external links or bookmarks our users have. 
- Add a line of text that says something like, "This page has been redirected to Topic Name." Use whatever text you like as long as the viewer is sent to the updated content. Removing the content and adding this message informs anyone who sees the old page in the repo/database that it's a redirected topic. When you commit your changes, add "Redirected page" or something similar in the commit changes title so that it's obvious in the file list that this is a redirected page.
- Ideally, submit a single Pull Request (PR) that contains all of the above commit changes together. Once the PR is submitted, email the [IoT Docs Site Managers](mailto:IOT-WOD@microsoft.com) a mapping of the old urls to the new urls, so we can put a permanent server redirect in place to clean up search results. (For an example, see this [redirected Docs page](https://github.com/ms-iot/content/blob/develop/en-US/win10/Docs.md)).

3. **Writing in markdown**

  For manageability and consistent look and feel, we enforce that our docs and samples be written in [Markdown](https://daringfireball.net/projects/markdown/basics). Complex formatting can be done with Liquid templates - details on those below.
   
  We will make exceptions to use html if needed.
  
  Good examples:

  * Docs: `content/en-us/docs/PowerShell.md` 
  * Samples: `content/en-us/samples/helloworld.md`

4. **Misc guidelines**

  * Use only one H1 (#) per topic / file
    * Very important for SEO
  * H1 and title (in the metadata) should be the same
    * (e.g. title: AllJoyn and `#AllJoyn`)
  * Fill out metadata
    * At the top of each file, you'll see a section starting and ending with "---" where metadata for that topic lives.  Fill this section with information pertaining to the topic you're working on.

## Making changes

Once you have [Git set up](/get-set-up.md), you can make changes to the repository.

For returning users, ensure that you are up to date with the ms-iot repo:

  `git fetch ms-iot`

  `git reset --hard ms-iot/develop`

  `git push origin develop`
  
**Note**: This will delete all local changes and push ms-iot to your fork, so be sure this is what you want

- Changes that do not follow the guidelines will be rejected
- Edit, build, test
  1. From within the content folder start a local server using *cmd.exe*
  
    `jekyll serve --incremental`
  2. If prompted by the firewall, allow Jekyll to serve content
  3. Open your web browser and point it to the local server. http://localhost:4000/content/en-US/iot.htm is the default page
    * **Note:** you won't see the correct formatting with a local server for certain aspects of the website:
        * Header/footer
        * Some margins
  
        this is to be expected. We still highly recommend rendering and verifying locally
  4. Edit using your favorite text editor. Jekyll will automatically update the content after every save
  5. If you are adding a new document, ensure that the files and images are saved in the correct folders
3. Commit changes 
  1. When ready, add the files you want to to be staged for commit:
    * `git add [file]`
  2. Once done, commit your changes:
    * `git commit -m "[descriptive message]" `

### Submitting a Pull Request

A pull request (PR) is a request to the ms-iot team to accept your changes. It must first be approved by the team, but once accepted, it will immediately go live.

1. Grab the latest changes from upstream

    `git fetch ms-iot`
    
2. Merge it into your local repository
    1. `git merge ms-iot/develop`
    2. If you run into conflicts, you will have to hand-merge (you can use your favorite merging tool or even notepad for this)
    3. After hand-merging, you can continue the merge
        * `git add [fileYouHandMerged]`
        
3. Check your repositories status
  * `git status`. You may need to continue the merge to finish

4. Push your changes to your forked repository.
    * `git push origin develop`
    
5. Submit your pull request from your forked repository using the GitHub website 

6. If it's your first pull request, sign the Contribution License Agreement 
  1.	Without completing this step, we unfortunately cannot accept a pull request. You only need to do this once 

### Making changes to a pull request

1. Make your new changes, fetch upstream, merge upstream, and push your changes
    * If your pull request was never closed, you should not have to submit a new pull request. It should automatically update
    
### Git guidelines

When evaluating PRs, the following guidelines must be met:

1. Must be auto-mergable.
    * You should have done the work so that we can automatically merge your changes with the current state of the repository. Otherwise we will reject your pull-request and wait until you have fixed it
    * If, after you make your changes and submit your PR, you find it cannot be automerged, simply update your fork with the latest from our repo and fix the conflicts - that should make it auto-mergable
2. Never have duplicate commits

### Publishing timelines

If there is a specific date or time that content needs publishing or if there is a pressing bug fix that needs merging ASAP, please email IOT-WOD@microsoft.com.

PRs submitted to our public repo will be evaluated and merged individually, usually within a few days of them being submitted.  Assume that once the PR is submitted, that content can go live anytime.

WOD moderators will take care of merging private content to public, usually in the middle of the month.  Specific date releases of private content must be communicated to stakeholders ahead of time, and give at least a **week** lead time to verify all parties are on board and verification can happen.


## Best Practices

### Do not check in binaries
Once a binary is added to the repository, it will be there forever.

Please do not add binaries to Git including:
* The output from a build (debug/release)
* SDF file (code database)
* Nuget package directories

Acceptable binaries:
* PNG, JPG, or other image formats

### Liquid templates and common files

Our build system supports liquid templates (those sections with the % signs in them).  This allows us to include commonly used snippets or insert a bit of html without needing to write it in manually.  The plus side is it allows us to use common things (think nice looking grid layouts or tables) or include a common sample in several different docs without copy/pasting.

These templates need to live within the _includes folder in the root, and are referenced by `{% include redirect.html url="http://www.microsoft.com" %}` which will insert whatever that file is at this point in your article.  You can add arguments or content to the include call. 

Examples on usage of [liquid basics](https://help.shopify.com/themes/liquid/basics) and the [liquid cheatsheet](http://cheat.markdunkley.com/) are a few pages that I find useful to learn about Liquid.

### Writing

There is much more that goes into a well written article than you'd think! Below are some suggestions of things to consider when proofreading your article.

**Voice**

Voice is, simply put, your writing style in terms of syntax, verbage, verbosity etc. When we're writing for the users of Windows IoT, we should align with the Windows Devices Group (WDG) [unified voice principles](https://worldready.cloudapp.net/StyleGuide/Read?id=2547). 

- **Warm and relaxed** We're natural. Less formal, more grounded in everyday conversations. Occasionally, we're fun (we know when to celebrate).
- **Crisp and clear** We're to the point. We write for scanning first, reading second. We make it simple above all.
- **Ready to lend a hand** We show customers we're on their side. We anticipate their real needs and offer great information at just the right time.
Also, please remember to **proof read.** Take a quick break from writing and review it with fresh eyes. You may find obvious mistakes that were not so obvious before.

**Title and headings** 

* Title and headings are **all sentence-case** (only first word and proper nouns capitalized).
* The **title should be an H1 (#)**. Only one H1 per topic.
* The **next level of headings should be H2 (##)**, and so forth. Don't skip heading levels.
* Avoid H4s, H5s, etc.

**Numbered lists and bulleted lists**

* **Use numbers to indicate steps** that go in a specific order (markdown = 1. Item, 2. Item).
* **Use bullets for lists** of unordered items (markdown = * item, or - item).
* **Use paragraphs** (no bullets or numbers) for text that’s not in a list.

**Terminology and abbreviations**
* **Use the same term throughout your doc**. Don't go back and forth between terms (such as “machine” and "computer" and "PC") when you are referring to the same thing. We have decided on the following terms: "Device" (referring to the Raspberry Pi board), "Peripheral" (for anything hooked up to the device/Raspberry Pi), and "PC" (referring to the computer). 
* **Do not abbreviate PowerShell** to PS unless it's part of a command. On first mention, use Windows PowerShell.
* **Do not abbreviate product names** unless there is a legally-approved acronym. *Official name of the Redstone 1 update to Windows 10: "Windows 10, version 1607". 
* **Spell out acronyms on first mention**, and include the acronym in parentheses. Thereafter, you can use the acronym by itself. 
**Example** – first mention: class identifier (CLSID); second mention: CLSID

**Formatting**
* **Use bold for UI entries**. (markdown = `**term**`)
Example: To start PowerShell as an administrator, right-click **Windows PowerShell**, and then select **Run as administrator**.
* **To emphasize a word, use italics**, not bold. (markdown = `*term*`)
* **For notes**, use the following liquid template: `{% include note.html text="This is a note" %}`
  * The same thing can be done with `tip.html`, and `warning.html`

**Links and cross-references**
* When you add a cross-reference, use this syntax: `For more information about *Foo*, see *Bar*.`
*Example:* "For a list of commands and utilities that you can use with PowerShell, see the [Command Line Utils]() page."
* **Format links** using the display name, not the URL, between the brackets: `[Display Name](URL)`.
* **Do not say, “Click here” or “Go here.”** Use the title of the page you’re pointing to.
* **Remove "en-us"** from TechNet and MSDN URLs (try them first). 
* **Remove ".htm"** from the any URL links. Do not use `https://developer.microsoft.com/en-us/windows/iot/docs/buildingappsforiotcore.htm`, instead use `https://developer.microsoft.com/en-us/windows/iot/docs/buildingappsforiotcore`. 
* **Add a "Related topics"** section (for topics in your repo) or "See also" or "Additional resources" section (for topics outside your repo) at the end of the page that at a minimum links back to your parent topic (to help users navigate).

**Images**
* **Resize your images** if they appear too big on stage or live.
* **Limit the number of your images** to only those you absolutely need to guide the user. Each image adds to page load time.

**SEO and Metadata**
Good metadata is an important factor in achieving good search results. The metadata for your .md markdown file should be located in a YAML block header at the top of the file.
```
---
layout: docs
title: Windows 10 IoT Core Dashboard
description: The best way to download, install and configure Windows 10 IoT Core
keyword: dashboard, Windows 10 IoT Core, download, install, configure
permalink: /en-US/Docs/IoTDashboard.htm
lang: en-US
---
```

Each topic, or markdown file, should have the properties, or metadata fields, listed above. The `title` and `description` fields are what appear in search results, so they should contain relevant keywords to help users find your content. 
  - **layout** Defines the page structure. Layout options can be found in the `_layouts` folder.
  - **`title`** Usually the same as your topic title (H1); however, the two can be different if you'd like to add additional keywords here to aid in search. 
    - Be concise, descriptive, and include the relevant target keywords. 
    - Use sentence-case capitalization. 
    - Maximum 70 characters. 
    - Appears as the title in search results.
  - **`description`** A complete sentence that uses relevant keywords and describes the intent of the page.
    - Include a call to action or entice a click-through from search to site.
    - Add synonyms that users might use to find your content.
    - Maximum 160 characters. 
    - Appears as the description in search results.
    - Note that while this field was originally populated with the WDCML `<abstract>` XML tag during the XMetaL migration, you may now update it and optimize it for search by using more descriptive copy as mentioned above.   
  - **`permalink`** The URL where this page will be found. The filename and permalink should always match.
  - **`lang`** Should always be set to en-US except for content translated by the localization team.
  
The YAML block renders into a table in markdown preview that you can view on the GitHub site. If it's not rendering correctly, check for the following:
- The YAML block must occur first in the markdown file between triple-dashed lines (before the H1), with no spaces or blank lines before it.
- Use lowercase for all metadata labels.
- Do not use colons except directly after the metadata label (do not use: `description: text: text`; use: `description: text...`)
- Do not duplicate the metadata label (for example: `description: description: text...`)
- Do not use brackets or any other characters such as quotation marks first in the metadata text (do not use: `description: [text] text...`; use: `description: Text [text] text`)
- Remove any apostrophes at the beginning and end of text that may have been imported in a copy/paste (for example: `title: 'text...'`)
- For the H1 (not in YAML block), only include the page title. Do not include metadata values (such as `msassetid`).
- The H1 must follow the YAML block with no other text between them; otherwise, the page may not render properly.

For more information, see the Windows Open Publishing Guide at http://aka.ms/windows-op-guide.

### References

1. [GitHub Documentation](https://help.github.com/)
2. [Git Cheatsheet!](https://github.com/github/training-materials/blob/master/downloads/github-git-cheat-sheet.pdf?raw=true)
3. [Git Documentation](http://www.git-scm.com/book/en/)
