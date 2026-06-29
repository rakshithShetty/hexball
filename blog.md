---
layout: page
title: Devlog
permalink: /blog/
---

Development updates, design decisions, and lessons learned building HexBall.

<ul>
  {% for post in site.posts %}
    <li>
      <span>{{ post.date | date: "%b %d, %Y" }}</span> —
      <a href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
