---
layout: page
title: notes
permalink: /notes/
---

### Recent Notes

<ul>
  {% for note in site.notes %}
    <li>
      <a href="{{ note.url }}">{{ note.title }}</a>
      <span style="color: #888;"> — {{ note.date | date: "%B %d, %Y" }}</span>
    </li>
  {% endfor %}
</ul>