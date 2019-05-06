---
layout: post
title:  "Multi-version add-in template with Revit 2020 support"
date:   2019-05-06 01:15:22 +0300
author: Salaros
categories: revit
tags:	revit .net addin visual-studio template
thumbnail: "/assets/posts/addin-template-with-2020-support/revit-addin-in-vs-debug-thumbnail.png"
cover: "/assets/posts/addin-template-with-2020-support/revit-addin-in-vs-debug.png"
---

Hey, it has been a long time since my last post [about .NET (Blazor + Visual Studio issue)](/dotnet/2019/02/17/blazor-cannot-identify-bin-folder).

This time I would like to share an updated version of the awesome [Revit add-in template](https://github.com/Equipple/vs-templates-revit-addin) I have created a while ago (BTW Jeremy Tammik [featured it on his blog](https://thebuildingcoder.typepad.com/blog/2018/07/vacation-and-multi-version-revit-add-in-template.html#2)).

Among other things this release includes:

* **Revit 2020** support
* the ability to **build & debug** one add-in at time
* binded new events
* simplified [Revit SDK NuGet](https://www.nuget.org/packages/Autodesk.Revit.SDK/) dependencies
* improved and simplified Ribbon management:
  * tab and panel management
  * the ability to use custom availability classes

I would 💖 **LOVE** 😍 to have some feedback from the community. Please use [project's issues](https://github.com/Equipple/vs-templates-revit-addin/issues) or by using [my contact details](/about-me).


#### ⬇⬇⬇ Template installation ⬇⬇⬇

Just grab the latest release (.zip file) from [releases page](https://github.com/Equipple/vs-templates-revit-addin/releases) and copy it into 
`"%USERPROFILE%\Documents\Visual Studio 2019\Templates\ProjectTemplates\Visual C#"` (use Visual Studio 2017 if you have that version)

<a href="/assets/posts/addin-template-with-2020-support/revit-addin-in-template-folder.png" data-lightbox="new-project" data-title="Template folder">
  <img src="/assets/posts/addin-template-with-2020-support/revit-addin-in-template-folder.png" title="Template folder">
</a>

<a href="/assets/posts/addin-template-with-2020-support/new-project-item-1.png" data-lightbox="new-project" data-title="New project dialog">
  <img src="/assets/posts/addin-template-with-2020-support/new-project-item-1.png" title="New project dialog">
</a>

<a href="/assets/posts/addin-template-with-2020-support/new-project-item-2.png" data-lightbox="new-project" data-title="New project dialog">
  <img src="/assets/posts/addin-template-with-2020-support/new-project-item-2.png" title="New project dialog">
</a>
