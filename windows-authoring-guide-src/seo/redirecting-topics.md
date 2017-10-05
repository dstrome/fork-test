---
author: traceylmnero
title: Redirecting topics
---
# Scheduling redirects and maintaining search authority

- creating a spreadsheet to map old to new URL paths for verification testing and permanent (301) redirection, 

- providing the staging URL on review.docs.microsoft.com to your SEO lead for review,

- a follow-up review with SEO lead to verify recommendations have been completed (est. 2-3 weeks before go live),

- a final SEO review 1 week post go live date.

- check for broken links
Broken links and 404s on the site give search engines a negative signal that affects the quality metric. 
Fix all in-line and navigation links that result in a 404 (page not found).



**This needs a re-write.**

<!-- OPS supports redirection at the topic level in MD (1-to-1 mapping between the old OP page URL to the new OP page URL). 
Reference [Master Redirection File](https://opsdocs.azurewebsites.net/en-us/opsdocs/partnerdocs/opredirection?branch=master#3-master-redirection-file)
 -->

> [!NOTE] 
> If you need to pave content for urgent business reasons, such as covering up premature feature disclosures, **[submit a ProdRequest](http://prodrequest)**.


**To redirect an OPS (MD) page level**:
- Be sure to update TOC.md to remove references to any topic that will redirect to a new one.

<!-- ## Topic-level redirection future process: use [Master Redirection File](https://opsdocs.azurewebsites.net/en-us/opsdocs/partnerdocs/opredirection?branch=master#3-master-redirection-file) -->

URL redirection - submission (estimate 5-10 days prior to go live)
- Create URL mapping file, for content that is to move from MSDN/Technet, for URL redirection submission to //MSDNHELP
- Cc Traceyw on URL redirection requset
- Provide [Traceyw](mailto:traceyw@microsoft.com) the URL mapping file to be referenced and for testing URLs redirects and testing URLs are refreshed in search indices. (est. 2-5 days before launch)

Update links (post launch - estimate 2-4 weeks)
- Coordinated effort - review existing links on site to ID links that have a redirect and update to the new destination URL path in order to reduce unneccesary redirects, which may hinder search crawler URL discovery. 
- This includes the update of links in UHF and core TOC navigation.

Update site search refinements on MSDN / Technet / Developer:
- Coordinated effort - review existing search refinements for landing pages remaining on MSDN / Technet / Developer
- Submit updated refinements - owner: Tracey Nero (estimate 2-5 days before go live)
- Testing refinements - owners:  SEO Lead, Channel Manager & Leads

Define site search scope on Docs.mscom:
- Coordinated effort - Channel Manager and SEO Lead define scenarios per audience
- Define scope labels for content sets (est. 1-3 weeks prior to go live)
- Scope implementation in MD at the Docset level / metadata topic level (est. 2-5 days prior to go live)

### VS China ownership:

URL redirection - execution
- //MSDNHELP - request redirects and provide URL mapping file of old to new URLs

Includes the following scenarios 
- MTPS – to OPS  (newly migrated to OP and going to Docs) 
- OP to OPS  (existing OP to Docs) 
- Streamlined topic level redirection via [Master file](https://opsdocs.azurewebsites.net/en-us/opsdocs/partnerdocs/opredirection?branch=master#3-master-redirection-file) solution in OPS. 


### Previous method to redirect individual topic(s): 
**Use this method if you need a quick setup of a redirect and having difficulty with MasterFile setup*

1. In the old OP page (the page you want to redirect), remove all the content except for the YAML block and the title (#H1).
2. In the YAML block, add `redirect_url` and add the new URL after the colon. This redirects the old page to the (new) page specified. Note that the target URL can be either absolute or relative. If the topic you're redirecting to isn't live yet, use the relative URL to avoid build issues. Note that in both instances, you should *not* include ".md" in the URL.
  
  Absolute URL (example):
   
     ```
     ---
     redirect_url: https://msdn.microsoft.com/virtualization/windowscontainers/
     ---
     ```
  Relative URL (example):
  
    ```
    ---
    redirect_url: /virtualization/windowscontainers/
    ---
    ```

3. Add a line of text that says something like, "This page has been redirected to *Topic Name*." Use whatever text you like as long as the viewer is sent to the updated content.
  
   Removing the content and adding this message informs anyone who sees the old page in the repo/database that it's a redirected topic. When you commit your changes, add "Redirected page" or something similar in the **commit changes** title so that it's obvious in the file list that this is a redirected page.

4. Keep the old page in the repo/database (because that's where the redirect lives). 
5. In the TOC.md file, remove the link to the old page (so that it no longer shows up in the live TOC).

<!-- For guidance about formatting links, see [Creating links](creating-links.md). -->


## MSDN/TechNet 301 permanent URL redirection (project-level redirection)

If you are planning to move content from MSDN/Technet:
- Plan ahead and capture all known URL paths in MSDN; for example: at `en-us/library/contentID` and at site scope level   `en-us/library/windows/hardware/contentID`.
- All URLs must be captured and mapped to destination URLs, which are defined with MSDN OPS team to land in the predefined (or newly defined) site scope.

Example: current MSDN (paved content) multiple mapping to single URL scenario:
- 1 path: `https://msdn.microsoft.com/en-us/library/windows/apps/dn726767.aspx`
- 2 path: `https://msdn.microsoft.com/en-us/library/dn726767.aspx`

Destination URL: within site scope
- `https://msdn.microsoft.com/en-us/windows/apps/xmal/whats-a-universal-windows-platform-uwp-app`

## Request MSDN/TechNet redirects for migrated content, or pave over and redirect any topic
Usually a lead or manager will handle requesting redirects for migrated content. If you're not sure, ask your manager or email [WDG CPUB Data & Analytics Open Publishing](mailto:winbitop@microsoft.com).

1.	Go to the [MSDNHelp partner support site](http://msdnhelp) and select **Library Support**.
2.	Under **Request Type**, select **Redirect**.
3.	Fill out the rest of the request and the required **Redirect template** (find this in the page intro), and then attach any files to the request.
4.	Click **Submit**. 
5.	An automatic email will be sent to your mailbox.
6.	If you have difficulties attaching the template to the request itself, you can reply to that email and attach the template to it.
7.	VSCOps will implement the redirects within five (5) business days depending on the volume. They will contact the person who opened the ticket to verify the results. 
