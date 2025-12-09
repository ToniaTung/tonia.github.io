---
layout: archive
title: "Projects"
permalink: /projects/
author_profile: true
---
{% include base_path %}

{% assign projects = site.portfolio | sort: "project_start" | reverse %}

{% for post in projects %}
  {% include archive-single.html type="list" %}
{% endfor %}
