---
author: jasongroce
description: Best practices for WinRT API reference documentation
title: API reference best practices
ms.author: jasgro
ms.topic: article
ms.prod: windows
ms.technology: uwp
---
# Best practices for WinRT API reference docs
The following is an attempt to break down what makes for API reference content that is most helpful for users.

> [!NOTE]
> The format and details of this list are under development, but the basic components have been adopted.

* Add “why” to remarks or description -  This method causes the geolocator to start producing location events. Use this if your app needs to track the device’s location over time.
* Overloads / APIs with the same root – Ensure language / defaults / remarks are consistent where appropriate. Ensure to disambiguate.
* Properties and method args
    * Default values
    * Null allowed?
    * Units
* Are expected values explained (if not an enum)? E.g. string values
* Are there preconditions before calling a method? (Either, procedurally or do I know how to get the object in the args)?
* Relation to other APIs. Particularly useful for events/event args. (MediaFrameReference -> “Use with MediaFrameReader, handle FrameArrived” - Relations like VSTS works items (dependent on, affected by, etc.)
* Links to how-to content. Can flow nicely with "why" remarks. 
* Shared code snippets with how-to content
* Initial state (AudioGraph nodes)
* Similarly named APIs that do different things (AudioTrackList vs. MediaPlaybackItemList, call out former is not a playlist but the latter is)
* Matching operations (start/stop) 