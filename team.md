---
title: Maintainers & Publications
description: Project maintainers, supervisors, research group, contact information, and representative service computing papers.
layout: benchmark
permalink: /team/
---

## Maintainers

<div class="model-grid compact-grid">
{% for member in site.data.team.maintainers %}
  <div class="model-card">
    <span>{{ member.role }}</span>
    <h3>{{ member.name }}</h3>
    <p>{{ member.affiliation }}</p>
    <a href="{{ member.homepage }}">Homepage</a>
  </div>
{% endfor %}
</div>

## Supervisor

<div class="model-grid compact-grid">
{% for member in site.data.team.supervisors %}
  <div class="model-card">
    <span>{{ member.role }}</span>
    <h3>{{ member.name }}</h3>
    <p>{{ member.affiliation }}</p>
    <p>{{ member.interests }}</p>
    <a href="{{ member.homepage }}">Homepage</a>
  </div>
{% endfor %}
</div>

## Research group

<div class="highlight-card compact">
  <h2>{{ site.data.team.group.name }}</h2>
  <p><strong>{{ site.data.team.group.affiliation }}</strong></p>
  <p>{{ site.data.team.group.description }}</p>
</div>

## Publications

<div class="publication-list">
{% assign papers = site.data.publications | sort: "year" | reverse %}
{% for paper in papers %}
  <article class="publication-card">
    <div class="pub-year">{{ paper.year }}</div>
    <div>
      <h3>{{ paper.title }}</h3>
      <p>{{ paper.authors }}. <em>{{ paper.venue }}</em>. <span>{{ paper.type }}</span></p>
      <div class="pub-links"><a href="{{ paper.pdf }}">PDF</a><a href="{{ paper.code }}">Code</a></div>
      <details><summary>BibTeX</summary><pre>{{ paper.bibtex }}</pre></details>
    </div>
  </article>
{% endfor %}
</div>

## Contact {#contact}

<div class="callout">
  <p><strong>Email:</strong> <a href="mailto:{{ site.data.contact.email }}">{{ site.data.contact.email }}</a></p>
  <p><strong>Issues:</strong> <a href="{{ site.data.contact.github_issues_url }}">GitHub Issues</a></p>
</div>
