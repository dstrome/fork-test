---
author: mikematteson
---
# Converting WDCML to markdown for open publishing  

> [!NOTE]
> This content is for information purposes only. If you need to migrate a WDCML project to markdown, please contact [Windows Open Publishing Support](mailto:winopsup).

This topic describes how to convert WDCML to markdown that validates and renders correctly in the MSDN Open Publishing environment. 
The preferred way to do this is by using the built-in support in the cbx build command. To do this:

1. Go to [IDWeb](https://idweb/identitymanagement/aspx/groups/AllGroups.aspx) and ensure that you are a member of the MSDN Reporting SG for your domain. You may need to wait up to 24 hours for permissions to propagate.
2. Install the latest release of [Pandoc](https://github.com/jgm/pandoc/releases). Pandoc is updated periodically, so if it's been a while since you installed it, consider upgrading. A recent fix improved table rendering, for example. By default, Pandoc installs to `c:\Users\<alias>\AppData\Local\Pandoc\`, which is added to your PATH.
3. Do an `sd sync` of your enlistment.
4. In a command window, type `con2md <project-name>` to build your project into .md files. The script will tell you the same prerequisites that are listed above.

 * The script builds the content twice and runs various cleanup and replacements each time; it also has to do a lookup of the MSDN database to replace all the xrefs with proper links. The whole conversion can take up to an hour for a project containing 1500 topics.
 * If the database pass fails, you will see:
  		Error connecting to db server. Ensure that you have perms on the MSDN Reporting SG.
 * Sometimes database access can be problematic. If you can't connect, try again a few hours later.

## Manual conversion

If you have problems with the automation, please send a bug report to DDPUB.  

The following steps are what the first pass above does. They are listed here for posterity.  

1. Fix links as follows:
	* Replace .htm link suffixes with .md, for in-project targets, for example:
		* `[Creating a Driver From Existing Source Files](creating_a_driver_from_existing_source_files.htm)`.  
	* Replace A keywords with URLs, for example:
		* `[Kernel-Mode Driver Framework](kmdf.portal)`
		* `<a href="wmi.mofcomp"><strong>mofcomp</strong></a>`
	* Remove **In This Section** links at the top.

2. Switch references to upper case **Images** directory to **images**: `![Visual Studio Solution Explorer Driver Package Project](images/VsSlnExplorer.png)`

3. Remove any %20 in URLs if they exist: `[MSBuild](%20http://go.microsoft.com/fwlink/p/?linkid=262804)`

4. If **See also** section is present, prepend asterisks to create bulleted list.

5. If existing, delete second occurrence of local target string: `[Manually installing WDTF on a test computer](dtf.runtime_library#manual_install_wdtf#manual_install_wdtf)`

6. Update embedded video links from: `![]()`
to look like this:

	```
	<iframe src="https://hubs-video.ssl.catalog.video.msn.com/embed/57464a96-8900-4194-b806-813eb1dd6ac6/IA?csid=ux-en-us&MsnPlayerLeadsWith=html&PlaybackMode=Inline&MsnPlayerDisplayShareBar=false&MsnPlayerDisplayInfoButton=false&iframe=true&QualityOverride=HD" width="720" height="405" allowFullScreen="true" frameBorder="0" scrolling="no"></iframe>
	```

7. Remove initial span so that OP creates correct topic title for text on browser tab: `<span id="vsdriver.avoiding_floating_point_errors_in_custom_build_environments"></span>`

8. Remove nested parenthetical version selector (v=vs.85, e.g.) from links: `[InfVerif](https://msdn.microsoft.com/en-us/Library/Windows/Hardware/Dn929319(v=vs.85).aspx)`

9. (Hardware team only) For mailto links, replace nested parentheses with %28, %29: `[Send comments about this topic to Microsoft](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20[VsDriver\vsdriver]:%20Analyzing%20a%20Driver%20Using%20Code%20Analysis%20and%20Verification%20Tools%20%20RELEASE:%20(9/30/2015)&body=...` <br/><br/>Topics that contain parentheses in the topic title also cause additional parentheses in the mailto link: `[Send comments about this topic to Microsoft](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20[VsDriver\vsdriver]:%20What%20happens%20when%20you%20provision%20a%20computer%20(WDK%208.0)%20%20RELEASE:%20%289/30/2015%29`

10. Remove extra carriage returns that occur after a **Note** inside a numbered list item, because it causes OP to start numbering again from "1." Leave one blank line remaining.

11. Remove copyright line: `© 2015 Microsoft. All rights reserved.`

12. Change any image file suffixes to lower case, for example: *.png*, not *.PNG*.

## Post-markdown conversion steps

- Create TOC.md in the parent directory.

## See also
- [Convert part of a WDCML project to markdown](partial-wdcml-to-open-publish.md)
- [WDCML to OP migration guide quick start](migration-quickstart.md)
- [Windows OP Guide TOC](../index.md)


<p>&nbsp;</p>
*Still have questions? Contact a human at [Windows Open Publishing Support](mailto:winopsup).*
