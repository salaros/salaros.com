---
layout: page
title: About me
permalink: /about-me/
---

<img src="{{ site.baseurl }}/assets/avatar.jpg" title="Salaros' picture" class="profile">

{% highlight none %}
    The text below in self-important "About me" page might contain way too many “I”, "me" or “my”.
    I apologize for abusing these terms :)
{% endhighlight %}

Hello, my name is **Yaroslav Zhmayev**, but you might also know me as **Salaros**.
I am an entrepreneur, startup-er, consultant and passionate full-stack software developer with **11+ years** of overall experience in IT.
I enjoy working in a challenging environment and under pressure, because I have great problem solving skills.
I am equally comfortable working as a member of a team (including distributed teams) as well as independently.

Even though I mainly work on enterprise solutions, I like giving back to the community by supporting my own open-source projects as well as
contributing to others projects. While pursuing my own personal development I do enjoy helping others to grow.

<div class="profiles">
{% for social in site.social %}
{% if social.url %}
<a href="{{ social.url }}" target="{{ social.target | default: '_blank' }}" title="{{ social.desc }}"><i class="fa fa-{{ social.icon | remove_first: '-square' }} fa-3x"></i></a>
{% endif %}
{% endfor %}
</div>