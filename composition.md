---
title: Service Composition
description: Task definition, QoS metrics, composition datasets, model families, and results for workflow-level service composition.
layout: benchmark
permalink: /composition/
---

## Task definition

Service composition converts complex user requirements into a service sequence, DAG, or executable workflow. Inputs include the user need, service library, functional constraints, input/output compatibility, and QoS constraints. The output should satisfy both functional requirements and non-functional optimization objectives.

<div class="callout"><strong>Key distinction:</strong> composition is not just Top-K retrieval; it produces an executable workflow whose quality depends on service compatibility and aggregated QoS.</div>

## Composition datasets

<div class="table-responsive">
<table class="benchmark-table">
  <thead><tr><th>Dataset</th><th>Domain</th><th>QoS</th><th>Requirement Type</th><th>Description</th></tr></thead>
  <tbody>
    <tr><td><strong>QWS</strong></td><td>Web Service</td><td>RT, TP, Availability, Reliability</td><td>Simulated requirements</td><td>Classic QoS service composition dataset.</td></tr>
    <tr><td><strong>WS-Dream</strong></td><td>Web Service</td><td>Response Time, Throughput</td><td>QoS prediction oriented</td><td>Can support recommendation, composition, and QoS prediction; functional semantics are weaker.</td></tr>
    <tr><td><strong>HSC</strong></td><td>AI Model Service</td><td>Metadata + QoS</td><td>Real-inspired workflows</td><td>Provides AI service workflows from Hugging Face model services.</td></tr>
    <tr><td><strong>HSC+</strong></td><td>AI Model Service</td><td>Response time, waiting time, reliability, successability</td><td>Generated realistic requirements and workflows</td><td>Core dataset for the benchmark.</td></tr>
  </tbody>
</table>
</div>

## Composition model library

<div class="model-grid">
{% for model in site.data.models.composition %}
  <div class="model-card">
    <span>{{ model.family }}</span>
    <h3>{{ model.name }}</h3>
    <p>{{ model.description }}</p>
    <a href="{{ model.code }}">Code</a>
  </div>
{% endfor %}
</div>

## QoS and workflow metrics

<div class="metric-list">
  <div><h3>Response Time ↓</h3><p>Total execution latency or path-level response time, typically aggregated along the workflow path.</p></div>
  <div><h3>Cost ↓</h3><p>Total service cost. If real cost is unavailable, the benchmark should define a simulated cost setting.</p></div>
  <div><h3>Throughput ↑</h3><p>Workflow throughput, often determined by the bottleneck service.</p></div>
  <div><h3>Availability ↑</h3><p>Probability that the composed service is available, commonly multiplied across component services.</p></div>
  <div><h3>Reliability ↑</h3><p>Probability of successful execution for the workflow.</p></div>
  <div><h3>Utility ↑</h3><p>Weighted normalized QoS score. The page should always document normalization and weights.</p></div>
</div>

## Composition results

<div class="leaderboard-controls" data-target="composition-table">
  <label>Dataset<select data-filter="dataset"><option value="">All</option><option>HSC+</option><option>QWS</option><option>WS-Dream</option></select></label>
  <label>Model Type<select data-filter="model_type"><option value="">All</option><option>Optimization-based</option><option>Learning-based</option><option>LLM-based</option></select></label>
</div>

<div class="table-responsive">
<table id="composition-table" class="benchmark-table filterable-table">
  <thead><tr><th>Model</th><th>Dataset</th><th>Type</th><th>Utility ↑</th><th>RT ↓</th><th>Cost ↓</th><th>Throughput ↑</th><th>Availability ↑</th><th>Reliability ↑</th><th>Code</th><th>Official</th><th>Unified Protocol</th></tr></thead>
  <tbody>
  {% for row in site.data.leaderboard_composition %}
    <tr data-dataset="{{ row.dataset }}" data-model_type="{{ row.model_type }}">
      <td><strong>{{ row.model }}</strong></td>
      <td>{{ row.dataset }}</td>
      <td>{{ row.model_type }}</td>
      <td>{{ row.utility }}</td><td>{{ row.response_time }}</td><td>{{ row.cost }}</td><td>{{ row.throughput }}</td><td>{{ row.availability }}</td><td>{{ row.reliability }}</td>
      <td><a href="{{ row.code }}">Link</a></td>
      <td>{{ row.official_reproduction }}</td>
      <td>{{ row.unified_protocol }}</td>
    </tr>
  {% endfor %}
  </tbody>
</table>
</div>
