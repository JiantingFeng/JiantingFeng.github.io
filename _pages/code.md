---
layout: page
permalink: /code/
title: Software & Code
description: Open-source software and research code
nav: true
nav_order: 5
---

## Research Software

### Active Projects
*Your active research software projects will be listed here*

### Archived Projects
*Your archived research software projects will be listed here*

## Open Source Contributions
*Your open source contributions will be listed here*

## GitHub Repositories

{% if site.data.repositories.github_repos %}
<div class="repositories d-flex flex-wrap flex-md-row flex-column justify-content-between align-items-center">
  {% for repo in site.data.repositories.github_repos %}
    {% include repository/repo.html repository=repo %}
  {% endfor %}
</div>
{% endif %}
