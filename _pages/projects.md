---
layout: page
title: projects
permalink: /projects/
description: A growing collection of my projects and research undertakings. 
nav: true
nav_order: 2
display_categories: [research, fun]
horizontal: false
---

<meta charset="UTF-8">

<style type="text/css">
<!--
a:link {color: #000000; text-decoration: none; }
a:active {color: #0000ff; text-decoration: none; }
a:visited {color: #000000; text-decoration: none; }
a:hover {color: red; text-decoration: none; }
-->
</style> 

{% for project in site.projects %}

  <p style="color:#737373"> &#128198; {{ project.date | date: "%b %Y"}}</p>
  <h3>
  <a href="{{ project.url }}">{{ project.title }}</a>
  <h3>
  <h6 style="color:#383838">{{ project.description }}</h6> 

  <hr>
  <br>
{% endfor %}


<!-- pages/projects.md -->
<div class="projects">
{%- if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized projects -->
  {%- for category in page.display_categories %}
  <h2 class="category">{{ category }}</h2>
  {%- assign categorized_projects = site.projects | where: "category", category -%}
  {%- assign sorted_projects = categorized_projects | sort: "importance" %}
  <!-- Generate cards for each project -->
  {% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-2">
    {%- for project in sorted_projects -%}
      {% include projects_horizontal.html %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for project in sorted_projects -%}
      {% include projects.html %}
    {%- endfor %}
  </div>
  {%- endif -%}
  {% endfor %}

{%- else -%}
<!-- Display projects without categories -->
  {%- assign sorted_projects = site.projects | sort: "importance" -%}
  <!-- Generate cards for each project -->
  {% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-2">
    {%- for project in sorted_projects -%}
      {% include projects_horizontal.html %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for project in sorted_projects -%}
      {% include projects.html %}
    {%- endfor %}
  </div>
  {%- endif -%}
{%- endif -%}
</div>
