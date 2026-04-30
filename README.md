# HSC-Bench GitHub.io Site

This repository is a Jekyll-based GitHub Pages website for **HSC-Bench: A Unified Benchmark for Service Recommendation and Service Composition**.

## Main pages

- `/` — homepage overview
- `/recommendation/` — service recommendation task, datasets, models, metrics, and results
- `/composition/` — service composition task, datasets, QoS metrics, models, and results
- `/hsc-plus/` — HSC+ dataset source, construction pipeline, schema, statistics, download, and citation
- `/leaderboard/` — centralized static leaderboards
- `/download/` — data, code, environment, quick start, and reproduction checklist
- `/team/` — maintainers, supervisors, publications, and contact information

## Data-driven files

- `_data/datasets.yml` — dataset metadata and download links
- `_data/models.yml` — recommendation and composition model library
- `_data/leaderboard_recommendation.csv` — recommendation leaderboard rows
- `_data/leaderboard_composition.csv` — composition leaderboard rows
- `_data/hscplus_schema.yml` — HSC+ schema
- `_data/hscplus_workflow.yml` — HSC+ construction pipeline
- `_data/publications.yml` — paper list and BibTeX
- `_data/team.yml` — maintainers, supervisors, research group

## Local development

```bash
bundle install
bundle exec jekyll serve
```

Open the local URL printed by Jekyll.

## Before public release

Replace all placeholder `TBD`, `#`, and example emails with final dataset links, GitHub repositories, paper links, team profiles, and benchmark results.
