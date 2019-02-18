---
layout: post
title:  "Cannot identify unique bin directory for Blazor app"
date:   2019-02-17 08:43:59
author: Salaros
categories: dotnet
tags:	blazor dotnet .net-core bug visual-studio
thumbnail: "/assets/posts/blazor-cannot-identify-bin-folder/error-w720.png"
---

As .NET developer I am pretty excited about Blazor and I am already using it in one of out prototypes.
However as many other alpha / preview libraries and frameworks it suffers from tiny yet annoying little bugs.
One of these bugs on Blazor its inability to switch from `Debug` to `Release` configuration seamlessly as other .NET project types do.
So after compiling the solution / project in `Debug` and then deploying it in `Release` mode you might see the following screen:

<a href="/assets/posts/blazor-cannot-identify-bin-folder/error.png" data-lightbox="blazor-large" data-title="Cannot identify unique bin directory for Blazor app">
  <img src="/assets/posts/blazor-cannot-identify-bin-folder/error-w720.png" title="Cannot identify unique bin directory for Blazor app">
</a>

As you can see it's [a known issue](https://github.com/aspnet/Blazor/issues/261), currently present in all versions of Blazor, including the latest preview version (0.8.0-preview-*) available at the time of writing this article.

Obviously you could manually remove `Debug` or `Release` folder depending on your current configuration or write a small tools which [does the same thing](https://youtu.be/UzEW0X8a010?t=1000) for you.

However you could automate the removal of the opposite / redundant folder by using good ol' MSBuild target.
Just drop the following [Directory.Build.targets](/assets/posts/blazor-cannot-identify-bin-folder/Directory.Build.targetsje) 
file into your Blazor app's solution root folder and you will never to take care about this error again.

<a href="/assets/posts/blazor-cannot-identify-bin-folder/solution.png" data-lightbox="blazor-large" data-title="Removing Release folder">
  <img src="/assets/posts/blazor-cannot-identify-bin-folder/solution.png" title="Removing Release folder">
</a>

Alternatively you might also integrate entire `<Target>` element inside your Blazor standalone .csproj file

{% highlight xml %}
<!-- A temporary workaround for the following Blazor bug: 
     https://github.com/aspnet/Blazor/issues/261 -->
<Target Name="RemoveOppositeOutputDirectoriesForBlazor"
        BeforeTargets="BeforeBuild" 
        Condition="$(RunArguments.Contains('blazor'))">
  <PropertyGroup>
    <OutputRoot>$(OutputPath)\..</OutputRoot>
    <!-- ReSharper disable once UnknownProperty -->
    <OutputRoot Condition="$(AppendTargetFrameworkToOutputPath)">
      $(OutputPath)\..\..
    </OutputRoot>
  </PropertyGroup>
  <ItemGroup>
    <OppositeOutputPath Include="$(OutputRoot)\Release" Condition="'$(Configuration)'=='Debug'" />
    <OppositeOutputPath Include="$(OutputRoot)\Debug" Condition="'$(Configuration)'=='Release'" />
  </ItemGroup>
  <Message Text="Removing the output folder of the opposite configuration: '@(OppositeOutputPath)'" 
            Importance="high" 
            Condition="Exists(@(OppositeOutputPath))" />
  <RemoveDir Directories="@(OppositeOutputPath)" />
</Target>
{% endhighlight %}
