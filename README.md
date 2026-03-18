# Project Tracking Dashboard

This directory hosts a repo-local static dashboard adapted from the
`yubol-bobo/Project_tracking` template.

## Public URL

After the GitHub Pages workflow deploys from `main`, the public dashboard URL is:

- `https://haonanhe.github.io/HOI3R/`

The deployed site serves the contents of this `project_tracking/` directory as the
site root.

## Source of Truth

Do not hand-edit `project_tracking/projects/hoi3r_submission.json` during normal
workflow. The dashboard data is generated from:

- `docs/NEURIPS_2026_SUBMISSION_PLAN.md`

## Regeneration

Run:

```bash
python scripts/export_project_tracking.py
```

This command updates:

- `project_tracking/projects/index.json`
- `project_tracking/projects/hoi3r_submission.json`

The GitHub Pages workflow publishes the committed contents of `project_tracking/`,
so regenerate the JSON before pushing plan updates that should appear on the
public dashboard.

## Purpose

This dashboard is a high-level overview surface for the HOI3R NeurIPS 2026
submission plan. Daily execution details remain in markdown planning docs and
Notion.
