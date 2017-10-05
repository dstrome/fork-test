---
author: mikematteson
---
# For writers: WDCML to OP migration quick start guide

In some cases, you might want to migrate part of a WDCML project to the open publishing platform. For example, sometimes a WDCML project contains both conceptual (overview) topics, as well as reference topics. If you want to move the conceptual pages to OP, but leave the reference in WDCML, use the following guide.

**This is a shortened version of [WDCML to OP migration guide](partial-wdcml-to-open-publish.md), for folks who are familiar with Git.  This short version is also the only actively maintained version.**

## Refactor the WDCML TOC (create OP and REF XTOC files)

To start, create two new XTOC files in your WDCML project:

* **projectname-OP.xtoc**: Holds the conceptual content that will be migrated to OP. Create it by copying your projectname.xtoc file.

* **projectname-REF.xtoc**: Holds the reference content that will continue being published in WDCML.

### Migration components

When all is done, the contents of the **projectname-REF.xtoc** file will replace the contents of the original **projectname.xtoc** file. You'll use the **projectname-OP.xtoc** file with **con2md.exe** to convert your content from WDCML to MD format. The conversion tool will also create a new **TOC.md** file for you. Finally, you can use **projectname-OP.xtoc** to create a redirects CSV file so that MSDN can remove those WDCML topics and redirect requests to the specified topics.

### Content architecture
While refactoring your project, it's helpful to consider the finished architecture. Because we're splitting conceptual and reference across two different platforms, you'll need to edit the site-wide Dev Center HXT and create a new WDCML parent topic (described later). 

![TOC relationship to HXT](images/HXTTOC.png)

This graphic is described in more detail when you go to edit the site-wide Dev Center HXT. For now, note that three different XTOC files play a part:

* **hw_nodes.xtoc**: Provides single-topic references to the new parent topics.
* **projectname-OP.xtoc**: The old WDCML topic GUID will guide people to OP via the MSDN redirects.
* **projectname.xtoc**: The end product (containing reference only) will supply the WDCML TOC.


> [!TIP]
> Try editing using XMetaL in tandem with VS Code to build your new XTOC files. In VS Code, you can collapse and copy whole TOC nodes.

You can use cbx to make sure that your new XTOCs build ok.

## Convert the conceptual topics to OP

Before you migrate, check for conditional topics or text in the project.  Deal with that manually.  For example, you might go ahead and convert conditional topics and then put them in a working branch in the private repo.

The **con2md.exe** tool resides in the BuildX\Cmd folder. 

Before you run con2md, you'll **TEMPORARILY** overwrite your projectname.xtoc file with your projectname-OP.xtoc file. 

    C:\SD\projectname>attrib -r projectname.xtoc

    C:\SD\projectname>copy projectname-OP.xtoc projectname.xtoc

To run the conversion, execute con2md as follows:

    C:\SD\projectname>con2md projectname

After it runs successfully, don't forget to go back and reload the projectname.xtoc file from SD using a forced resync:

    C:\SD\projectname>sd sync -f ...

### Moving the TOC.md file
Now copy the TOC.md down a level into the folder named after the project.

Then, remove the name of the project folder from the file paths. For example, the NFC TOC.md file originally looked like this:

    # [NFC design guide](nfpdrivers/nfc-design-guide.md)
    ## [What's new in NFC device drivers](nfpdrivers/what-s-new-in-nfc-device-drivers.md)  
    ## [NFC architecture](nfpdrivers/nfc-architecture.md)

But after removing the folder from the file path, it now looks like:

    # [NFC design guide](nfc-design-guide.md)
    ## [What's new in NFC device drivers](what-s-new-in-nfc-device-drivers.md)  
    ## [NFC architecture](nfc-architecture.md)

> [!TIP]
> Note that you are **free to rename the project folder!** For example, we renamed *nfpdrivers* to be simply *nfc* in the repo.

### Rename your TOP-most parent topic
If you don't specify the file name in an OP URL, MSDN will serve up the index.md file if it exists. 

1. Find your top-most parent topic and rename it to be **index.md**.
2. In TOC.md, change the name of the source file to be **index.md**.
3. Do a search of the MD files for any links to the previous file name. You can use the findstr utility with CMD.exe to find any occurrences of that file name. For example, if the old topic was named introduction.md, the findstr command would be:

        c:\SD\projectname\build\markdown\mdout>findstr /S /I /M /C:"introduction.md" *.md

4. Finally, it is suggested that you add a Related topics link that points back to the project's WDCML reference content, as was done in the [NFC design guide](https://msdn.microsoft.com/en-us/windows/hardware/drivers/nfc/nfc-design-guide). If users end up on index.md, they may not have an easy way back to unmigrated reference content.


### Add the newly converted files to the repo 

In your local clone, create a new branch and copy over your md files, images, and TOC.md.

> [!WARNING]
> Your new TOC.md should have no more than six levels of indentation.  Search for ####### to test yours.

You can name your new OP directory the same as the old WDCML project, or change it to be more meaningful. Keep in mind, the folder name appears in the OP URL. 

    C:\myrepo\drivers [master]> .\.openpublishing.build.ps1 -parameters:targets=serve

    Open your browser to -->  [http://localhost:8080](http://localhost:8080)

### Add breadcrumbs

In the `windows-driver-docs-pr\breadcrumbs` directory, add an entry to `toc.yml` for your new node.

### Fix rendering issues caused by `\<`

In your new MD directory, run `select-string '(?<!\\)\\<'` to look for rendered `\<`.  You might want to change some of the occurrences to render as `\\<`.  But this includes results in code blocks, which should probably be left as-is.

Also note that Pandoc might prepend a backslash in front of underscore characters.  Consider searching for occurrences of `\_` and replacing them with just `_`.  You can use VS Code to do the replacement.

Also replace `&amp;` with `&`.

### Push your local working repo to the team repo
Push your working branch up to origin and verify that it builds ok. 

### Compare content against WDCML
Click through your OP topics and see that they render well. If you like, build a CHM of projectname-OP.xtoc file and compare topics with the OP versions.

### Add your project to the top level TOC in OP
The OP driver documentation, the Windows Driver Kit (WDK) topic, resides here:

[https://msdn.microsoft.com/en-us/windows/hardware/drivers](https://msdn.microsoft.com/en-us/windows/hardware/drivers)

To make your project appear in the TOC, you need to add it to the TOC.md file located at the root of your directory:

        C:\myrepo\drivers\windows-driver-docs-pr\TOC.md

## Build a .CSV file for redirecting old topics to OP
The CSV should look like this:

```
"msdnID","locale","Product family version","Target URL"
"019ABD43-601C-4C1B-A0D9-30A3A402650C","en-us","","https://msdn.microsoft.com/windows/hardware/drivers/bringup/bring-up"
```

Be sure you don't include any conditionally removed topics in the CSV.

> [!NOTE]
> Don't forget to change the target URL of the top topic to point to index.md.

Wait until you go to publish all the changes to Live before you submit the redirect request.  At the time of writing, Subbu Devalla is the contact for redirects.  You'll find more details below on submitting the request.

> [!NOTE]
> For more info about the CSV format, see the MSDN [Redirect template](https://microsoft.sharepoint.com/teams/Visual_Studio_China/MSDN/msdnpartner/_layouts/15/WopiFrame.aspx?sourcedoc=%7bCDDAB058-5F12-4C24-B931-E13A62FFDAF4%7d&file=Redirection%20Template.docx&action=default).


## Create a new WDCML parent topic in HW_NODES

First, create an FWLink for testing on MSDNStage.  You'll put the FWLink in the new HW_NODES topic.  Initially, it will point to the staged index topic.  

You may want to copy the contents from an existing HW_NODES topic that does the same thing, like `hw_nodes\near_field_communication_devices.xml`.

Be sure to add your new HW_NODES topic to hw_nodes.xtoc.  You'll publish that project later.

## Update WDCML TOC to show only reference topics
Now that you have OP content and a new WDCML parent topic, the next step is to make your WDCML project **reference only**. If you've already created your projectname-REF.xtoc file, all you need to do is:

1. **Check out** your projectname.xtoc file.

2. **Overwrite** your project TOC with the new REF TOC.  

        C:\SD\projectname>copy projectname-REF.xtoc projectname.xtoc

3. **Check in** your projectname.xtoc file.


## Create a local copy of the Dev Center HXT file and add new OP and REF

The site-wide HXT is saved in SD here (assuming your enlistment folder is on C:\SD):

    C:\SD\BuildX\MTPS\en-us\hardware_dev_center.hxt

For your technology, the new HXT elements will include three parts:

* **A new parent topic**: A single-topic reference to the WDCML topic in hw_nodes.xtoc.
* **The OP content**: A single-topic reference to the GUID of the old conceptual topic that will be redirected to OP (index.md).
* **The Reference content**: A TOC reference to the WDCML project defined by projectname.xtoc.

To prepare a new Dev Center HXT file:

1. Re-sync the BuildX folder. 

2. Copy the HXT file somewhere other than BuildX where you can edit the file. 

3. Make it writeable:

        C:\your-file-editing-folder>attrib -r hardware_dev_center.hxt

4. Search for the current reference to your project in the HXT.

5. Paste the following template below that reference:  

    ```
    <!-- TECHNOLOGYNAME device drivers -->
    <!-- Parent topic from HW_NODES WDCML project -->
    <HelpTOCNode NodeType="Regular" Title="TECHNOLOGYNAME device drivers" Url="AssetID:PARENTGUID ^VS.85">

        <!-- TECHNOLOGYNAME driver design guide from Open Publishing platform -->
        <HelpTOCNode NodeType="Regular" Title="TECHNOLOGYNAME driver design guide" Url="AssetID:CONCEPTUALGUID ^VS.85"/>

        <!--TECHNOLOGYNAME DDI reference content from WDCML platform -->
        <HelpTOCNode NodeType="TOC" Url="VS|PROJECTNAME|$\PROJECTNAME.hxt@0 ^VS.85" />

    </HelpTOCNode>
    ```

    A few notes about this XML:  
    * The **NodeType** indicates the kind of reference. **Regular** means it's a single-topic reference. *TOC* means the entire child hierarchy is defined by the referenced HXT (your projectname.xtoc).
    * The **Title** element specifies the text **in the TOC nav** and overrides whatever is written in the contents of the specified file. In other words, the title at the top of the page has no bearing on what appears in the TOC nav. The Title is needed when NodeType is TOC - the title is inferred from the contents of the project HXT.

6. Replace the placeholder values with those from your project. Of course, feel free to change the text in the comments and titles where it makes sense. But if possible, try to make them consistent with what it was before.   

    * **PARENTGUID**: The MSDN ID (the GUID) from the WDCML parent topic in HW_NODES.
    * **CONCEPTUALGUID**: The MSDN ID (the GUID) of the WDCML topic that was converted to be the new OP parent topic (renamed to be index.md).
    * **PROJECTNAME**: The name of the WDCML project now holding only reference topics. You can simply copy/paste to replace the PROJECTNAME line with the old HXT reference to your project.

7. After you're finished revising that TOC node, delete the old HXT reference above the new one.

8. Save the changes. 


### Pre-deployment checklist:
* OP content in working branch looks good on MSDNStage.
* WDCML redirects CSV file is complete and ready to go (including index rename for parent topic).
* Updated copy of HXT file is ready to go.
* You've reviewed SD history to make sure that no WDCML changes were made after the conversion.
* You've reviewed the new WDCML parent topic in HW_NODES (use the GUID to navigate directly to it on Stage).
* The FWlink to OP content is pointing to OP working branch on Stage.

### Conversion sequence
The process from this point on looks like this:  


2. Submit Prodrequest to update Stage with revised hardware_dev_center.hxt, hw_nodes, and your WDCML project.  

3. In the TOC nav of Stage, verify that:   
    * Technology link points to new parent in HW_NODES.  
    * Design guide link points to the orphaned WDCML single-topic target (the top conceptual topic that will redirect to OP).  

4.  Publish OP content externally  
    1. First merge your *working-branch* to *Master*.  If it's been a while, merge master into working first.  When you merge working to master, you might want to squash.
    2. Review on MSDNStage.
    3. Merge *Master* to *Live*.

4. Update your FWLINK (recall it is in the hw_nodes topic) to point to the root index of the new live OP content.  Note that you must wait until the hw_nodes topic is live, and the OP target is live.

5. Update your Prodrequest - ask them to push the changes to *Live*.

6. Submit redirects CSV on MSDNHelp.

7. Review the changes on the Live environment.

8. Move old WDCML to the Archive folder in Source Depot.



## Clean up: Move old WDCML content to Source Depot Archive folder

Now you need to use `sd integrate` and `sd delete` to move the WDCML files that you migrated to the SD archive:

`//depot/DevDoc/archive/`

If you are archiving an entire WDCML project, you should also search for the project name and remove it if it appears in any of the following files:

```
SDROOT\buildx\schema\xsd\validtechvalues.xsd
SDROOT\buildx\script2\config\adjustments_projectlevel.xml
SDROOT\buildx\script2\config\*tech*.xml
SDROOT\buildx\script2\templates\indexing_boilerplates.xslt
SDROOT\*.txt
```


### How to submit a ProdRequest for MSDNStage:
1. Open your browser to [http://prodrequest](http://prodrequest).

2. Fill out the web form as follows:
    * Click **New request**.
    * What type of request? = **Production services**
    * Area = **WDCML/Library**
    * Request = **Other**
    * For Title consistency, try to use **HXT update for WDCML to OP migration (projectname)**
    * For Additional information, use this template (keep hw_nodes in there if applicable). You may or may not want to put a time limit on the request before proceeding, as shown:  

        ```
        [Note: If this can't be completed today, please do not proceed with this request]

        Please update the Staging environment with the following changes:

        1. Update the Master hardware_dev_center.hxt with the changes specified in the attached HXT file. The Master hardware_dev_center.hxt file is located in Source Depot here:                  
            //depot/DevDoc/Main/BuildX/mtps/en-us/hardware_dev_center.hxt

        2. Re-build these projects: projectname, hw_nodes

        3. Push to Stage: projectname, hw_nodes, hardware_dev_center.hxt

        Please wait and do not push these changes to Live until the changes can be verified in the staging environment.

        Thanks!
        ```

3. Click **Submit** and wait for the email to arrive.
4. After the email arrives, navigate to the VSO work item and add your modified HXT file to the task.
5. Don't forget to click **Save** after you attach your HXT file.    


## Submitting the redirect request

Here's how to submit the redirect request to MSDN using MSDN Help.  You might want to do these steps in Internet Explorer, because in Edge, the drag and drop at the end to add your .csv to the request may not work.

1. Go to [http://msdnhelp](http://msdnhelp).  

2. Click **Library Support**.

3. In the form, fill out these values:  

   * Set **Work request title** something to the effect of..  

            WDCML redirect request for projectname OP migration
   * **Request Type** = Redirect  

   * **Priority** = 1  

   * Set **Description** to something like..  

        	One or more WDCML projects was recently migrated to OP and published to Live. Please remove the WDCML topics at the specified GUIDs and redirect requests to the specified URLs/GUIDs.

	        Please expedite these redirects. Until these redirects are performed, our site-wide TOC will not be working as intended.

            Thank you!

4. Click **Submit**.  

5. On the following page, drag your CSV file (created earlier) from Windows Explorer onto the web page where you can add the attachment.  

6. Click **Done** to add the CSV attachment

When the redirects go live, your link in the HXT to the design guide, which points to the MSDN ID of the old WDCML design guide root topic, will be automatically redirected to the OP root.
