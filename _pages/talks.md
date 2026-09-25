---
layout: page
permalink: /talks/
title: Talks
description: Conferences attended and talks given.
nav: true
nav_order: 3
---

<div class="talks">
  {% assign sorted_talks = site.data.talks | sort: "date" | reverse %}
  {% if sorted_talks.size > 0 %}
    <ul class="talk-list">
      {% for talk in sorted_talks %}
        <li>
          <strong>{{ talk.title }}</strong>{% if talk.type %} &mdash; {{ talk.type }}{% endif %}<br />
          {{ talk.event }}{% if talk.location %}, {{ talk.location }}{% endif %}{% if talk.date %} &middot; {{ talk.date }}{% endif %}
          {% if talk.url %} &middot; <a href="{{ talk.url }}" target="_blank" rel="noopener">link</a>{% endif %}
        </li>
      {% endfor %}
    </ul>
  {% else %}
    <p>Coming soon.</p>
  {% endif %}
</div>
