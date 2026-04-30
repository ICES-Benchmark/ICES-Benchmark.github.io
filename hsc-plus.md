---
title: HSC+ Dataset
description: Dataset source, construction pipeline, schema, statistics, task support, download, and citation for HSC+.
layout: benchmark
permalink: /hsc-plus/
---

## Overview

HSC+ is a large-scale AI model service dataset built from Hugging Face model services. It provides unified service metadata, refined functional annotations, QoS measurements, generated user requirements, and executable service workflows for service recommendation and service composition.

<div class="highlight-card compact">
  <h2>Core value</h2>
  <p>HSC+ is designed as a shared data resource for three connected research problems: service recommendation, service composition, and QoS analysis.</p>
</div>

## Construction pipeline

<div class="timeline-grid">
{% for item in site.data.hscplus_workflow %}
  <div class="timeline-item">
    <span>{{ item.step }}</span>
    <h3>{{ item.name }}</h3>
    <p>{{ item.description }}</p>
  </div>
{% endfor %}
</div>

## Data schema

<div class="table-responsive">
<table class="benchmark-table">
  <thead><tr><th>Field</th><th>Description</th></tr></thead>
  <tbody>
  {% for item in site.data.hscplus_schema %}
    <tr><td><code>{{ item.field }}</code></td><td>{{ item.description }}</td></tr>
  {% endfor %}
  </tbody>
</table>
</div>

## Statistics to publish

<div class="metric-list">
  <div><h3>Service categories</h3><p>Number of models under each Hugging Face task category.</p></div>
  <div><h3>Downloads and likes</h3><p>Popularity distributions showing long-tail service usage patterns.</p></div>
  <div><h3>Loading / waiting time</h3><p>Average loading time across model types.</p></div>
  <div><h3>Response time</h3><p>Average, minimum, and maximum response time by service type.</p></div>
  <div><h3>Status code distribution</h3><p>HTTP 200, 400, 403, 500, 503 and other response status ratios.</p></div>
  <div><h3>Reliability and successability</h3><p>Distribution of stable successful invocations and valid task completions.</p></div>
  <div><h3>Workflow length</h3><p>Complexity distribution of generated service workflows.</p></div>
  <div><h3>Requirement length and type</h3><p>Diversity of natural-language user requirements generated for workflows.</p></div>
</div>

## Task support

<div class="row g-4">
  <div class="col-12 col-md-4"><div class="info-card"><h3>Recommendation</h3><p>Requirement-to-service and mashup-to-service matching with Top-K evaluation.</p></div></div>
  <div class="col-12 col-md-4"><div class="info-card"><h3>Composition</h3><p>Input/output compatible workflow generation and QoS-aware optimization.</p></div></div>
  <div class="col-12 col-md-4"><div class="info-card"><h3>QoS Analysis</h3><p>Response time, waiting time, reliability, successability, and status code analysis.</p></div></div>
</div>

## Download and citation

The public dataset link, version number, checksum, and license should be filled in before release.

<div class="cta-row">
  <a class="button button-primary" href="{{ site.data.contact.dataset_url }}">Dataset Link</a>
  <a class="button button-secondary" href="{{ '/download/' | relative_url }}">Reproduction Guide</a>
</div>

```bibtex
@inproceedings{hscbench2026,
  title     = {HSC-Bench: A Comprehensive Benchmark for Unified Service Recommendation and Composition Evaluation},
  author    = {TBD},
  booktitle = {TBD},
  year      = {2026}
}
```
