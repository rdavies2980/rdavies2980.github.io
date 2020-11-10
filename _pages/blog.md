---
title: "Blog Posts"
permalink: /blogtags/
layout: archive
---

This blog is meant to pull together various bits of information that I have realised while studying Physics. Not every post is an earth shattering revelation - more a small realisation! I thought it worth collecting these thoughts as working my way through these various problems took a while so hopefully this will speed up someone else's realisations!

Here is a list of all of the posts to the blog organised by the various topics that they contain

{% for tag in site.tags %}
  {% assign t = tag | first %}
  {% assign posts = tag | last %}

{{ t | downcase }}
<ul>
{% for post in posts %}
  {% if post.tags contains t %}
  <li>
    <a href="{{ post.url }}">{{ post.title }}</a>
    <span class="date">{{ post.date | date: "%B %-d, %Y"  }}</span>
  </li>
  {% endif %}
{% endfor %}
</ul>
{% endfor %}
