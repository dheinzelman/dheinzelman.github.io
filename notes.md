---
layout: term
title: notes
permalink: /notes/
cmd: ls -l notes
---

<table>
  {% for note in site.notes %}
  <tr class="ls-l">
    <td>-rw-r--r--</td>
    <td>1</td>
    <td>{{ site.author.name }}</td>
    <td>{{ note.content | number_of_words }}</td>
    <td class="date">{{ note.date | date: "%b %d %H:%M" }}</td>
    <td>
      <a href="{{ note.url }}">{{ note.title }}</a>
    </td>
  </tr>
  {% endfor %}
</table>