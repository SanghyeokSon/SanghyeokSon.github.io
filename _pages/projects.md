---
layout: page
title: projects
permalink: /projects/
description: A collection of my projects in reversed chronological order.
nav: true
nav_order: 3
---

<!-- _pages/projects.md -->

<div class="projects">

{% assign sorted_projects = site.projects | sort: "year" | reverse %}
{% assign current_year = "" %}

{% for project in sorted_projects %}
  {% if project.year != current_year %}
    {% unless forloop.first %}</ol>{% endunless %}
    <h2 class="year">{{ project.year }}</h2>
    <ol class="bibliography">
    {% assign current_year = project.year %}
  {% endif %}

  <li>
    <div class="project-item">
      {% if project.redirect %}
        <a href="{{ project.redirect }}"><strong>{{ project.title }}</strong></a>
      {% else %}
        <a href="{{ project.url | relative_url }}"><strong>{{ project.title }}</strong></a>
      {% endif %}
      {% if project.description %}
        <div class="project-description">{{ project.description }}</div>
      {% endif %}
    </div>
  </li>

  {% if forloop.last %}</ol>{% endif %}
{% endfor %}

</div>
