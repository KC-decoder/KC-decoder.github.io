---
layout: page
title: REFLECTIONS
permalink: /reflections/
description: A collection of personal reflections and insights.
nav: true
nav_order: 3
display_categories: [personal, professional]
horizontal: false
---

<!-- pages/reflections.md -->
<div class="reflections">
{%- if site.enable_reflection_categories and page.display_categories %}
  <!-- Display categorized reflections -->
  {%- for category in page.display_categories %}
  <h2 class="category">{{ category }}</h2>
  {%- assign categorized_reflections = site.reflections | where: "category", category -%}
  {%- assign sorted_reflections = categorized_reflections | sort: "importance" %}
  <!-- Generate cards for each reflection -->
  {% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-2">
    {%- for reflection in sorted_reflections -%}
      {% include reflections_horizontal.html %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for reflection in sorted_reflections -%}
      {% include reflections.html %}
    {%- endfor %}
  </div>
  {%- endif -%}
  {% endfor %}

{%- else -%}
  <!-- Display reflections without categories -->
  {%- assign sorted_reflections = site.reflections | sort: "importance" -%}
  <!-- Generate cards for each reflection -->
  {% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-2">
    {%- for reflection in sorted_reflections -%}
      {% include reflections_horizontal.html %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for reflection in sorted_reflections -%}
      {% include reflections.html %}
    {%- endfor %}
  </div>
  {%- endif -%}
{%- endif -%}
</div>
