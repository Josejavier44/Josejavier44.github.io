---
layout: page
permalink: /conferences/
title: Conferences & Schools
description: Conferences and summer/winter schools attended.
nav: true
nav_order: 4
---

<div class="conferences">
  {% assign sorted_conferences = site.data.conferences | sort: "date" | reverse %}
  {% if sorted_conferences.size > 0 %}
    <ul class="conference-list">
      {% for event in sorted_conferences %}
        <li>
          <strong>{{ event.title }}</strong>{% if event.type %} &mdash; {{ event.type }}{% endif %}<br />
          {% if event.location %}{{ event.location }}{% endif %}{% if event.date %} &middot; {{ event.date }}{% endif %}
          {% if event.url %} &middot; <a href="{{ event.url }}" target="_blank" rel="noopener">link</a>{% endif %}
        </li>
      {% endfor %}
    </ul>
  {% else %}
    <p>Coming soon.</p>
  {% endif %}
</div>
