---
author: traceylmnero
title: Adding required metadata for SEO & BI reporting
---
# Adding required metadata 

Required metadata is added via a YAML block and is used for both SEO and BI reporting purposes (via SkyEye). 

- The metadata YAML block MUST be the first thing in the MD file.
- The metadata YAML block MUST take the form of valid YAML set between triple-dashed lines.

Example metadata YAML block:
```
---
title: WinRT API authoring: Markdown and linking
description: Get set up for authoring WinRT API ref 
author: ghalias
ms.author: msalias
ms.date: 2/03/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp (use the name of the content area the topic fits in to)
keywords: windows 10, uwp, WinRT API
---
```

### Core key metadata requirements for all markets
To meet minimum compliance with SEO and BI metadata, the following metadata should be stubbed in the new OPS files. 

|**Metadata tag**|**Value**|**Required**|
|---|---|---|
|author|Refers to the GitHub alias for the content owner/writer|Yes|
|description|A complete sentence or two that uses relevant keywords and describes the intent of the page. Consider including a call to action to entice a click-through from search to site (max 160 characters).|Yes|
|title|Page title is usually the same as the topic title (H1); however may be different to include additional keywords or messaging to aid in search.|Yes|
|ms.author|Refers to the Microsoft alias for the content owner/writer|Yes|
|ms.date|Date this topic was authored/updated.|No|
|ms.topic|Use "article" for all conceptual content.|Yes|
|ms.prod|Used by BING and filtered search to identify content based on operating system--use "windows" for all uwp content.|Yes|
|ms.technology|Name of the content area your topic fits in to, ie. "UWP"|Yes|
|keywords|Should include the topic along with supporting synonyms or phrases which may help with search categorization.|No|
|ms.assetid|Used only for topics migrating from MTPS to OPS for URL redirection using //MSDNHELP & CX BI reporting.|No|
| 

- All metadata labels are lower case.
- All metadata attributes should be followed by a colon and a space.
- *Avoid including additional characters, such as a single or double quotes around the copy for each tag " ' "*
- Each page should have an unique title within the recommended character limit of 59 characters or less. *Exceptions may be made for titles that must be longer to convey accurate meaning, such as an API name reference.

> [!NOTE]
> A page title suffix will be auto-generated at the end of your page title unique to your content set to support product and content set grouping for search and data tracking, this will increase the overall title length by ~31 characters.
> For example, "UWP app developer" differentiates content from "Win32 API Ref" content. 

## YAML block tips

The YAML block renders into a table in markdown preview. If it's not rendering correctly, check for the following:
- The YAML block must occur first in the markdown file between triple-dashed lines (before the H1), with no spaces or blank lines before it.
- Use lowercase for all metadata labels. (Required)
- Do not use colons except directly after the metadata label (do not use: `description: text: text`; use: `description: text...`)
- Do not duplicate the metadata label (for example: `description: description: text...`)
- Do not use brackets or any other characters such as quotation marks first in the metadata text (do not use: `description: [text] text...`; use: `description: Text [text] text`)
- Remove any apostrophes at the beginning and end of text that may have been imported in a copy/paste (for example: `title: 'text...'`)
- For the H1 (not in YAML block), only include the page title. Do not include metadata values.
- The H1 must follow the YAML block with no other text between them; otherwise, the page may not render properly.

## Docset level metadata in docfx.json

You can override default metadata in the "fileMetadata" and "globalMetadata" docfx.json file so that ALL files under the docset will have the meta applied. This is used for metadata such as page title suffix that will be applied to the entire set of documentation.


Global page title suffix, in docfx.json:
```
    "globalMetadata": {
        "titleSuffix": "UWP app developer",
              "searchScope": ["UWP"],
              "hideScope": true
    },
```


File pattern metadata:
```
    "fileMetadata": { 
       "titleSuffix": 
       { 
        "api/**.yml": "Azure" ,
         "input-and-devices/**.yml": "Azure Solutions" ,
         "intro/**.yml": "Azure Overview" 
       } 
     }, 
```

## Additional metadata tags

- Meta robots: indexed content vs. noindex content: By default, the page will be set to Index content. On content you do not want to have discoverable in search, change this meta data setting at a docset level using docfx.json file. *ROBOTS is an exception in formatting YAML block labels as it needs to be in UPPER case.*- ms.lang: Language of the content, automatically generated
- ms.loc: Locale of the topic, automatically generated

## Additional SEO and Accessibility tips:

- **Only a single # H1 allowed**: Write your primary heading using target keywords that best describe what the page topic covers and possible action item for web visitors, such as "UWP Code Samples" or "Windows 10 SDK Download". Avoid writing topic title (H1) as generic copy such as "Downloads" or "Samples".
- **Images**: `![Alt text](images/file-name.png)`: Every image requires an alt text which provides a brief description of the image in the context of the page copy. 