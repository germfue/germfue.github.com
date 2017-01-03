---
layout: page
title: Blog
permalink: /blog/
---

<ul class="post-list">
{% for post in site.posts %}
    {% if post.layout == "post" %}
<li>
<span class="post-meta">{{ post.date | date: "%b %-d, %Y" }}</span>
<a class="post-link" href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>            
</li>
<div> {{ post.excerpt }} </div>
<a class="post-link" href="{{ post.url | prepend: site.baseurl }}">continue...</a>            
    {% endif %}
{% endfor %}
</ul>
