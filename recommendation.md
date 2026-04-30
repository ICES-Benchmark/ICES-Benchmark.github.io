---
title: Service Recommendation
description: Task definition, datasets, models, metrics, and results for unified Top-K service recommendation evaluation.
layout: benchmark
permalink: /recommendation/
---

## Task definition

Service recommendation takes a user requirement, mashup description, service library, service tags, service descriptions, and optional QoS attributes as input. The output is a Top-K candidate service list. HSC-Bench documents candidate-set scope, train/validation/test split strategy, and recommendation generation logic so that models are compared under the same protocol.

<div class="callout"><strong>Output format:</strong> ranked service IDs with scores, evaluated at configurable K values such as 5 and 10.</div>

## Recommendation datasets

<div class="table-responsive">
<table class="benchmark-table">
  <thead><tr><th>Dataset</th><th>Task Support</th><th>Domain</th><th>Main Fields</th><th>Page Notes</th></tr></thead>
  <tbody>
  {% assign rec_datasets = "ProgrammableWeb,HSC,HSC+,MovieLens,Amazon" | split: "," %}
  {% for dataset in site.data.datasets %}
    {% if rec_datasets contains dataset.name %}
    <tr>
      <td><strong>{{ dataset.name }}</strong></td>
      <td>{{ dataset.tasks }}</td>
      <td>{{ dataset.domain }}</td>
      <td>{{ dataset.fields }}</td>
      <td>{{ dataset.note }}</td>
    </tr>
    {% endif %}
  {% endfor %}
  </tbody>
</table>
</div>

## Recommendation model library

<div class="model-grid">
{% for model in site.data.models.recommendation %}
  <div class="model-card">
    <span>{{ model.family }}</span>
    <h3>{{ model.name }}</h3>
    <p>{{ model.description }}</p>
    <a href="{{ model.code }}">Code</a>
  </div>
{% endfor %}
</div>

## Evaluation metrics

<div class="metric-list">
  <div><h3>Precision@K ↑</h3><p>Fraction of Top-K recommended services that match ground-truth services.</p></div>
  <div><h3>Recall@K ↑</h3><p>Fraction of ground-truth services covered by the Top-K list. This is important when a mashup has multiple target services.</p></div>
  <div><h3>F1@K ↑</h3><p>Harmonic mean of Precision@K and Recall@K for balanced comparison.</p></div>
  <div><h3>NDCG@K ↑</h3><p>Ranking-sensitive metric that rewards correct services appearing earlier in the list.</p></div>
  <div><h3>MRR ↑</h3><p>Mean reciprocal rank of the first correct recommendation, emphasizing early hits.</p></div>
</div>

## Recommendation results

Use the filters below to inspect the CSV-backed static leaderboard. Replace `TBD` values after final experiments are available.

<div class="leaderboard-controls" data-target="recommendation-table">
  <label>Dataset<select data-filter="dataset"><option value="">All</option><option>HSC+</option><option>ProgrammableWeb</option><option>MovieLens</option><option>Amazon</option></select></label>
  <label>Model Type<select data-filter="model_type"><option value="">All</option><option>Traditional</option><option>Neural</option><option>Graph-based</option><option>LLM-based</option><option>Benchmark Model</option></select></label>
</div>

<div class="table-responsive">
<table id="recommendation-table" class="benchmark-table filterable-table">
  <thead><tr><th>Model</th><th>Dataset</th><th>Type</th><th>P@5</th><th>P@10</th><th>R@5</th><th>R@10</th><th>NDCG@5</th><th>NDCG@10</th><th>MRR</th><th>Code</th><th>Official</th><th>Unified Split</th></tr></thead>
  <tbody>
  {% for row in site.data.leaderboard_recommendation %}
    <tr data-dataset="{{ row.dataset }}" data-model_type="{{ row.model_type }}">
      <td><strong>{{ row.model }}</strong></td>
      <td>{{ row.dataset }}</td>
      <td>{{ row.model_type }}</td>
      <td>{{ row.p5 }}</td><td>{{ row.p10 }}</td><td>{{ row.r5 }}</td><td>{{ row.r10 }}</td><td>{{ row.ndcg5 }}</td><td>{{ row.ndcg10 }}</td><td>{{ row.mrr }}</td>
      <td><a href="{{ row.code }}">Link</a></td>
      <td>{{ row.official_reproduction }}</td>
      <td>{{ row.unified_split }}</td>
    </tr>
  {% endfor %}
  </tbody>
</table>
</div>
