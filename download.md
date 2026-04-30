---
title: Download & Reproduction
description: Data links, code repositories, environment setup, evaluation scripts, and minimal commands for reproducing HSC-Bench results.
layout: benchmark
permalink: /download/
---

## Data downloads

<div class="table-responsive">
<table class="benchmark-table">
  <thead><tr><th>Dataset</th><th>Version</th><th>Tasks</th><th>Files</th><th>Download</th></tr></thead>
  <tbody>
  {% for dataset in site.data.datasets %}
    <tr>
      <td><strong>{{ dataset.name }}</strong></td>
      <td>{{ dataset.version }}</td>
      <td>{{ dataset.tasks }}</td>
      <td>{{ dataset.fields }}</td>
      <td><a href="{{ dataset.download }}">Link</a></td>
    </tr>
  {% endfor %}
  </tbody>
</table>
</div>

## Code repositories

<div class="row g-4">
  <div class="col-12 col-md-4"><div class="info-card"><h3>Benchmark Core</h3><p>Data loaders, split definitions, evaluation scripts, and submission templates.</p><a href="{{ site.data.contact.code_url }}">Repository</a></div></div>
  <div class="col-12 col-md-4"><div class="info-card"><h3>Recommendation Baselines</h3><p>Traditional, neural, graph-based, and LLM reranking implementations.</p><a href="{{ site.data.contact.code_url }}">Repository</a></div></div>
  <div class="col-12 col-md-4"><div class="info-card"><h3>Composition Baselines</h3><p>Optimization, learning-based, and agentic workflow generation implementations.</p><a href="{{ site.data.contact.code_url }}">Repository</a></div></div>
</div>

## Environment

Recommended release metadata:

- Python: `3.10+`
- PyTorch / CUDA: fill in per model release
- Evaluation scripts: versioned with the benchmark repository
- Random seed and hardware: reported in every result card

## Quick start

```bash
# 1. Prepare datasets
python scripts/prepare_data.py --dataset hsc_plus --version v1

# 2. Run service recommendation
python run_recommendation.py --config configs/recommendation/srlcf_hsc_plus.yaml

# 3. Run service composition
python run_composition.py --config configs/composition/gnnpn_sc_hsc_plus.yaml

# 4. Evaluate and export leaderboard rows
python scripts/evaluate.py --task recommendation --pred outputs/recommendation.jsonl
python scripts/evaluate.py --task composition --pred outputs/composition.jsonl
```

## Reproduction checklist

<div class="metric-list">
  <div><h3>Dataset version</h3><p>Record exact version, checksum, and preprocessing script commit.</p></div>
  <div><h3>Unified split</h3><p>Use official train/validation/test split for fair comparison.</p></div>
  <div><h3>Configuration</h3><p>Publish YAML config, random seed, model hyperparameters, and hardware.</p></div>
  <div><h3>Logs and outputs</h3><p>Attach raw predictions, evaluation logs, and generated leaderboard row.</p></div>
</div>
