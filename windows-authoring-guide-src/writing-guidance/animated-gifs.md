---
author: mattwoj
description: How to create and publish animated gifs in windows
title: How to create and publish animated GIFs
ms.author: mattwoj
ms.topic: article
ms.prod: windows
---

# How to Create and Publish Animated GIFs

This topic describes the process for creating and publishing animated GIFs.

## Why use animated GIFs?
- GIFs can instruct users, illustrate problems for customer support, or mock up a new idea for the design process.
- GIF screen captures are easy to create.
- GIFs are natively supported by effectively all browsers, unlike many video formats and players, so your audience doesn’t need to install a plug-in to see it.
- Compared to a sequence of still images, GIFs are less cognitively demanding. Your viewer doesn’t have to mentally interpolate frames between still images because the frames actually exist. For example, trying to follow step-by-step drawings of how to tie a knot can be much more challenging than watching an animated equivalent.
- GIFs can be embedded pretty much anywhere and be reasonably expected to work. So you can use a GIF in a technical document just as easily as in a tweet or an email.

## Guidelines for using animated GIFs
GIFs should be:

- **Used sparingly.** Many animations visible on screen can be distracting or confusing, especially if they’re mixed with other text. Too much visual noise from competing animations can hinder your audience’s ability to appreciate anything on screen.
- **Small.** GIF isn’t an efficient image format and can cause slow page load speed, so keep your file sizes in check. If overused, GIFs can cause your page size to balloon out of control.
- **Short.** If a GIF goes longer than 5 seconds, video may be a better format to pursue.
- **Demonstrative in nature.** The GIF should show what something is or what it does, but without the expectation that the viewer is meant to be able to reproduce the demonstration themselves.
- **Used for familiarization.** It should acquaint the viewer with something that they’re going to do themselves, but with the expectation that more detail is forthcoming.
- **Alt text.** Animated GIFs should contain alt text, just like you would enter for an image. Alt text should provide the text-equivalent to any non-text visuals included in the GIF, or anything that a visually-impaired user would need to understand the content without being able to see it. Including alt text will also help animated GIFs to show up in search results.

## Accessibility considerations
W3C Web Content Accessibility Guidelines outline two sections that should be considered when using animated GIFs:

- [Guideline 2.2](http://www.w3.org/TR/WCAG20/#time-limits) - Enough Time: Includes guidelines around "Pause, Stop, Hide" and "Auto-updating."
- [Guideline 2.3](http://www.w3.org/TR/WCAG20/#seizure) - Seizures: Do not design content in a way that is known to cause seizures.

Animation can cause significant distractions for users with cognitive disabilities. For those with a high degree of motion sensitivity, flash rates between 2hz – 55hz can cause an epileptic seizure.

In regard to blind or visually impaired users, "Alt" tags or content text should supplement any animated GIF explaining any content being demonstrated in the animation.

To address these issues, developers must provide accessible, non-animated methods for disabling or pausing animated content within a page.

## Tools
For an excellent outline of animated-GIF-creation methods, tools and optimization techniques, including how to create aGIFs with Photoshop, see [CSSTricks "Makin GIFs"](https://css-tricks.com/makin-gifs/).

The following tools can be helpful for creating aGIFs:

- **Screen capture:** [LICEcap](http://www.cockos.com/licecap/) captures part of your screen and saves the result as an animated GIF.
- **Converting still images to GIF:** [ImageMagick](http://www.imagemagick.org/script/index.php) is a suite of tools for creating and manipulating images. The animate command can be used to stitch together many individual still images (for example, a series of screenshots or photos) into an animated GIF.
- **Optimizing file size and performance:** [Online GIF Optimizer](http://gifmaker.me/optimizer/) can help you reduce your GIF file size and allows you to choose the level to optimize color, frame rate, and lossyness. [Gifsicle](http://www.lcdf.org/gifsicle/) is a command-line tool that can significantly reduce your GIF’s file size (also see the [documentation manual](https://www.lcdf.org/gifsicle/man.html)). Lastly, this tutsplus article outlines [10 Ways to Optimize an Animated GIF File](http://design.tutsplus.com/tutorials/10-ways-to-optimize-an-animated-gif-file--psd-34649).
- **Setting the number of times a GIF repeats:** [Gifsicle](http://www.lcdf.org/gifsicle/) has a feature baked in to enable you to set the loopcount (see these [instructions](https://davidwalsh.name/prevent-gif-loop)).

## Adding code to enable start/stop capability for GIFs
You can add code to do the following:

- **Play animated GIFs on click:** [Tutorial](http://www.hongkiat.com/blog/on-click-animated-gif/), with an [example page](http://hongkiat.github.io/gif-onclick/) showing this method in use, and the [code in GitHub repo](https://github.com/hongkiat/gif-onclick) (requires jQuery 85kb library)
- **Play animated GIFs on hover:** [Tutorial.](http://docs.embed.ly/docs/tutorial-play-and-stop-gifs) Requires [Embedly API](http://docs.embed.ly/docs/libraries) – lots of ways to include.
- **Add via plain vanilla JS:** Haven't found a code example yet (this [stackoverflow article](http://stackoverflow.com/questions/5818003/stop-a-gif-animation-onload-on-mouseover-start-the-activation) explains how to load a static image, and then switch to animated GIF on hover).

## Examples
- [Pause/play GIF on hover with jQuery](http://codepen.io/CalebGrove/pen/bIsqy) (Codepen)
- [Use as a new way of good app presentation](http://designmodo.com/animated-gif-app-presentation/) (Slides Framework)

## Related articles
- [GIFs as Documentation:](http://gifs-as-documentation.readthedocs.io/en/latest/) A short guide to using GIFs in documentation and as documentation.
- [Designing Safer Web Animation For Motion Sensitivity:](http://alistapart.com/article/designing-safer-web-animation-for-motion-sensitivity) Outlines reasoning for accessibility concerns, how GIFs can affect those with motion sensitivity, and guidelines for designing safer motion on the web.
- [Microsoft Accessibility Course: Animated Images:](https://learn.microsoft.com/rgcontents/CONT15249/scormcontent/class/ms/non-text-content/alt-text/animations.html#video-audio-motion_animations_prerecorded-video-only_autoplay) This course slide covers the currently recommend practices for using animated images.