---
layout: page
title: projects
permalink: /projects/
description: Our lab studies how microbes and host cells interact within complex tissues. We develop computational approaches that integrate genomics, spatial biology, and mathematical modeling to better understand infection, inflammation, and disease. We also build standardized pipelines for 16S microbiome meta-analysis to identify microbial taxa and community patterns that shape host biology. 
Beyond host–microbe interactions, we investigate genome rearrangements and somatic alterations in cancer, developing computational methods and analysis pipelines to uncover the genomic events driving tumor evolution and disease.
We welcome students from diverse backgrounds who are interested in computational biology. Whether you want to learn scripting, high-performance computing (HPC), cancer genomics, microbiome analysis, or cutting-edge spatial transcriptomics, there are many opportunities to contribute to ongoing research while developing practical computational and data science skills. If you're interested in joining our team, we'd love to hear from you.
nav: true
nav_order: 3
display_categories: [work]
horizontal: false
---

<!-- pages/projects.md -->
<div class="projects">
{% if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized projects -->
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>
  {% assign categorized_projects = site.projects | where: "category", category %}
  {% assign sorted_projects = categorized_projects | sort: "importance" %}
  <!-- Generate cards for each project -->
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_projects %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
  {% endif %}
  {% endfor %}

{% else %}

<!-- Display projects without categories -->

{% assign sorted_projects = site.projects | sort: "importance" %}

  <!-- Generate cards for each project -->

{% if page.horizontal %}

  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_projects %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
  {% endif %}
{% endif %}
</div>
