---
layout: page
permalink: /talks/
title: Talks
description: Talks given at seminars, workshops, and conferences.
nav: true
nav_order: 3
---

<div class="talks">
  {% assign all_talks = site.data.talks %}
  {% assign outreach_talks = all_talks | where: "audience", "Outreach" %}
  {% assign research_talks = all_talks | where_exp: "t", "t.audience != 'Outreach'" %}

  <h2>Research talks</h2>
  {% assign sorted = research_talks | sort: "date" | reverse %}
  {% if sorted.size > 0 %}
    <ul class="talk-list">
      {% for talk in sorted %}
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

  <h2>Outreach talks</h2>
  {% assign sorted = outreach_talks | sort: "date" | reverse %}
  {% if sorted.size > 0 %}
    <ul class="talk-list">
      {% for talk in sorted %}
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
