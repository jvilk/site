---
layout: page
title: Blog
excerpt: "An archive of blog posts sorted by date."
---

Thoughts on research, complex software systems, and other things.

<ul class="post-list">
{% for post in site.categories.blog %}
  <li><article><a href="{{ site.url }}{{ post.url }}">{{ post.title }} <div class="entry-date"><time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%B %d, %Y" }}</time></div></a>{{ post.excerpt }}</article></li>
{% endfor %}
</ul>
