---
layout: page
title: projects
permalink: /projects/
description: A collection of my projects in reversed chronological order.
nav: true
nav_order: 3
---

<!-- _pages/projects.md -->

<div class="publications">

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
    <div class="row">
      <div class="col-sm-10">
        <div class="title">
          {% if project.redirect %}
            <a href="{{ project.redirect }}">{{ project.title }}</a>
          {% else %}
            <a href="{{ project.url | relative_url }}">{{ project.title }}</a>
          {% endif %}
        </div>
        {% if project.description %}
          <div class="periodical">{{ project.description }}</div>
        {% endif %}
        <div class="links">
          {% if project.redirect %}
            <a href="{{ project.redirect }}" class="btn btn-sm z-depth-0" role="button">Link</a>
          {% else %}
            <a href="{{ project.url | relative_url }}" class="btn btn-sm z-depth-0" role="button">Details</a>
          {% endif %}
        </div>
      </div>
    </div>
  </li>

  {% if forloop.last %}</ol>{% endif %}
{% endfor %}

</div>
