---
layout: page
title: classes
permalink: /classes/
description: University teaching.
nav: true
nav_order: 3
display_categories: [gis]
horizontal: false
---

<!-- pages/classes.md -->
<div class="classes">
{%- if site.enable_classes_categories and page.display_categories %}
  <!-- Display categorized classes -->
  {%- for category in page.display_categories %}
  <h2 class="category">{{ category }}</h2>
  {%- assign categorized_classes = site.classes | where: "category", category -%}
  {%- assign sorted_classes = categorized_classes | sort: "importance" %}
  <!-- Generate cards for each class -->
  {% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-2">
    {%- for class in sorted_classes -%}
      {% include classes_horizontal.html %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for class in sorted_classes -%}
      {% include classes.html %}
    {%- endfor %}
  </div>
  {%- endif -%}
  {% endfor %}

{%- else -%}
<!-- Display classes without categories -->
  {%- assign sorted_classes = site.classes | sort: "importance" -%}
  <!-- Generate cards for each class -->
  {% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-2">
    {%- for class in sorted_classes -%}
      {% include classes_horizontal.html %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for class in sorted_classes -%}
      {% include classes.html %}
    {%- endfor %}
  </div>
  {%- endif -%}
{%- endif -%}
</div>
