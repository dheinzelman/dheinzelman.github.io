---
layout: term
title: notes
permalink: /notes/
cmd: ls -la notes
---

Recent Notes

<div class="term">
  <table>
    {% for note in site.notes %}
    <tr class="ls-la">
      <td class="date">{{ note.date | date: "%b %d %Y" }}</td>
      <td>
        <a class="file" href="{{ note.url }}">{{ note.title }}</a>
      </td>
    </tr>
    {% endfor %}
  </table>
</div>