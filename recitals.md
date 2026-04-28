---
layout: page
title: Recitals
permalink: /recitals/
---

### Upcoming

{% assign curDate = site.time | date: '%s' %}
<div class="recitals">
{% for post in site.posts %}
  {% assign postStartDate = post.date | date: '%s' %}
  {% if postStartDate > curDate %}
    <div class="archive-item">
    <span class="post-date archive-date fs-4"
        >{{ post.date | date: "%d %B, %Y" }}</span
    >
    <a href="{{ post.url | relative_url }}" class="archive-title fs-4"
        >{{ post.title }}</a
    >
    </div>
  {% endif %}
{% endfor %}
</div>

### Past

{% assign now = site.time | date: '%s' %}
{% assign current_year = "" %}

<div class="recitals">
{% for post in site.posts %}
  {% assign post_time = post.date | date: '%s' %}
  {% assign post_year = post.date | date: "%Y" %}

  {% if post_time <= now %}

    {% if post_year != current_year %}
      <h1 class="archive-year">{{ post_year }}</h1>
      {% assign current_year = post_year %}
    {% endif %}

    <div class="archive-item">
      <span class="post-date archive-date fs-4">
        {{ post.date | date: "%d %B, %Y" }}
      </span>
      <a href="{{ post.url | relative_url }}" class="archive-title fs-4">
        {{ post.title }}
      </a>
    </div>

  {% endif %}
{% endfor %}
</div>