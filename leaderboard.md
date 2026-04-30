---
title: Leaderboard
description: Centralized benchmark results for service recommendation and service composition, with static filters for the first release.
layout: benchmark
permalink: /leaderboard/
---

## How to read the leaderboard

The first release uses static CSV-backed tables. Results should specify dataset, model type, code availability, official reproduction status, and whether the result follows the unified split or protocol.

<div class="leaderboard-tabs">
  <a href="#recommendation">Service Recommendation</a>
  <a href="#composition">Service Composition</a>
</div>

## Service Recommendation {#recommendation}

<div class="leaderboard-controls" data-target="leaderboard-rec-table">
  <label>Dataset<select data-filter="dataset"><option value="">All</option><option>HSC+</option><option>ProgrammableWeb</option><option>MovieLens</option><option>Amazon</option></select></label>
  <label>Model Type<select data-filter="model_type"><option value="">All</option><option>Traditional</option><option>Neural</option><option>Graph-based</option><option>LLM-based</option><option>Benchmark Model</option></select></label>
</div>

<div class="table-responsive">
<table id="leaderboard-rec-table" class="benchmark-table filterable-table">
  <thead><tr><th>Model</th><th>Dataset</th><th>Type</th><th>K</th><th>P@5</th><th>P@10</th><th>R@5</th><th>R@10</th><th>NDCG@5</th><th>NDCG@10</th><th>MRR</th><th>Code</th><th>Paper</th></tr></thead>
  <tbody>
  {% for row in site.data.leaderboard_recommendation %}
    <tr data-dataset="{{ row.dataset }}" data-model_type="{{ row.model_type }}">
      <td><strong>{{ row.model }}</strong></td><td>{{ row.dataset }}</td><td>{{ row.model_type }}</td><td>{{ row.k }}</td>
      <td>{{ row.p5 }}</td><td>{{ row.p10 }}</td><td>{{ row.r5 }}</td><td>{{ row.r10 }}</td><td>{{ row.ndcg5 }}</td><td>{{ row.ndcg10 }}</td><td>{{ row.mrr }}</td>
      <td><a href="{{ row.code }}">Code</a></td><td><a href="{{ row.paper }}">Paper</a></td>
    </tr>
  {% endfor %}
  </tbody>
</table>
</div>

## Service Composition {#composition}

<div class="leaderboard-controls" data-target="leaderboard-comp-table">
  <label>Dataset<select data-filter="dataset"><option value="">All</option><option>HSC+</option><option>QWS</option><option>WS-Dream</option></select></label>
  <label>Model Type<select data-filter="model_type"><option value="">All</option><option>Optimization-based</option><option>Learning-based</option><option>LLM-based</option></select></label>
</div>

<div class="table-responsive">
<table id="leaderboard-comp-table" class="benchmark-table filterable-table">
  <thead><tr><th>Model</th><th>Dataset</th><th>Type</th><th>Utility ↑</th><th>RT ↓</th><th>Cost ↓</th><th>Throughput ↑</th><th>Availability ↑</th><th>Reliability ↑</th><th>Code</th><th>Paper</th></tr></thead>
  <tbody>
  {% for row in site.data.leaderboard_composition %}
    <tr data-dataset="{{ row.dataset }}" data-model_type="{{ row.model_type }}">
      <td><strong>{{ row.model }}</strong></td><td>{{ row.dataset }}</td><td>{{ row.model_type }}</td>
      <td>{{ row.utility }}</td><td>{{ row.response_time }}</td><td>{{ row.cost }}</td><td>{{ row.throughput }}</td><td>{{ row.availability }}</td><td>{{ row.reliability }}</td>
      <td><a href="{{ row.code }}">Code</a></td><td><a href="{{ row.paper }}">Paper</a></td>
    </tr>
  {% endfor %}
  </tbody>
</table>
</div>

## Submission protocol

1. Use the official dataset version and split.
2. Run the published evaluation script with fixed random seed and configuration.
3. Add a row to the corresponding CSV file.
4. Submit a pull request with paper link, code link, configuration, logs, and hardware information.
