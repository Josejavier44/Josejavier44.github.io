---
layout: page
permalink: /conferences/
title: Conferences & Schools
description: Conferences and summer/winter schools attended.
nav: true
nav_order: 4
---

<div class="courses">
  {% assign sorted_conferences = site.data.conferences | sort: "date" | reverse %}
  {% if sorted_conferences.size > 0 %}
    <div class="course-list">
      {% for event in sorted_conferences %}
        <div class="course-item">
          <h3 class="course-title">{{ event.title }}</h3>
          <div class="course-meta">
            {% if event.type %}<span class="course-term">{{ event.type }}</span>{% endif %}
            {% if event.date %}<span class="course-instructor">{{ event.date }}</span>{% endif %}
          </div>
          <div class="course-description">
            <p>
              {{ event.location }}
              {% if event.url != blank %} &middot; <a href="{{ event.url }}" target="_blank" rel="noopener">link</a>{% endif %}
            </p>
          </div>
        </div>
      {% endfor %}
    </div>
  {% else %}
    <p>Coming soon.</p>
  {% endif %}
</div>
