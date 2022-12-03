---
layout: page
title: HackTheBox Challenges
permalink: /hackthebox/
description: A growing collection of your cool hackthebox.
nav: true
nav_order: 2
display_categories: [work, fun]
horizontal: false
---

<!-- pages/hackthebox.md -->
<div class="hackthebox">
{%- if site.enable_hackthebox_categories and page.display_categories %}
  <!-- Display categorized hackthebox -->
  {%- for category in page.display_categories %}
  <h2 class="category">{{ category }}</h2>
  {%- assign categorized_hackthebox = site.hackthebox | where: "category", category -%}
  {%- assign sorted_hackthebox = categorized_hackthebox | sort: "importance" %}
  <!-- Generate cards for each hackthebox -->
  {% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-2">
    {%- for hackthebox in sorted_hackthebox -%}
      {% include hackthebox_horizontal.html %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for hackthebox in sorted_hackthebox -%}
      {% include hackthebox.html %}
    {%- endfor %}
  </div>
  {%- endif -%}
  {% endfor %}

{%- else -%}
<!-- Display hackthebox without categories -->
  {%- assign sorted_hackthebox = site.hackthebox | sort: "importance" -%}
  <!-- Generate cards for each hackthebox -->
  {% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-2">
    {%- for hackthebox in sorted_hackthebox -%}
      {% include hackthebox_horizontal.html %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for hackthebox in sorted_hackthebox -%}
      {% include hackthebox.html %}
    {%- endfor %}
  </div>
  {%- endif -%}
{%- endif -%}
</div>
