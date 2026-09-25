---
layout: page
permalink: /talks/
title: Talks
description: Talks given at seminars, workshops, and conferences.
nav: true
nav_order: 3
---

<div class="courses">
  {% assign all_talks = site.data.talks %}
  {% assign outreach_talks = all_talks | where: "audience", "Outreach" %}
  {% assign research_talks = all_talks | where_exp: "t", "t.audience != 'Outreach'" %}

  <h2 class="year">Research talks</h2>
  {% assign sorted = research_talks | sort: "date" | reverse %}
  {% if sorted.size > 0 %}
    <div class="course-list">
      {% for talk in sorted %}
        <div class="course-item">
          <h3 class="course-title">{{ talk.title }}</h3>
          <div class="course-meta">
            {% if talk.type %}<span class="course-term">{{ talk.type }}</span>{% endif %}
            {% if talk.date %}<span class="course-instructor">{{ talk.date }}</span>{% endif %}
          </div>
          <div class="course-description">
            <p>
              {{ talk.event }}{% if talk.location %}, {{ talk.location }}{% endif %}
              {% if talk.url != blank %} &middot; <a href="{{ talk.url }}" target="_blank" rel="noopener">link</a>{% endif %}
            </p>
          </div>
        </div>
      {% endfor %}
    </div>
  {% else %}
    <p>Coming soon.</p>
  {% endif %}

  <h2 class="year">Outreach talks</h2>
  {% assign sorted = outreach_talks | sort: "date" | reverse %}
  {% if sorted.size > 0 %}
    <div class="course-list">
      {% for talk in sorted %}
        <div class="course-item">
          <h3 class="course-title">{{ talk.title }}</h3>
          <div class="course-meta">
            {% if talk.type %}<span class="course-term">{{ talk.type }}</span>{% endif %}
            {% if talk.date %}<span class="course-instructor">{{ talk.date }}</span>{% endif %}
          </div>
          <div class="course-description">
            <p>
              {{ talk.event }}{% if talk.location %}, {{ talk.location }}{% endif %}
              {% if talk.url != blank %} &middot; <a href="{{ talk.url }}" target="_blank" rel="noopener">link</a>{% endif %}
            </p>
          </div>
        </div>
      {% endfor %}
    </div>
  {% else %}
    <p>Coming soon.</p>
  {% endif %}
</div>
