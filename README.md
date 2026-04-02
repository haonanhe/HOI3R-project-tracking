# Project Tracking Dashboard

This directory hosts a repo-local static dashboard adapted from the
`yubol-bobo/Project_tracking` template.

## Public URL

The public dashboard is hosted from the mirror repository:

- Site: `https://haonanhe.github.io/HOI3R-project-tracking/`
- Mirror repo: `https://github.com/haonanhe/HOI3R-project-tracking`

The mirror repository serves the contents of this `project_tracking/` directory as
the site root.

## Milestone Nodes

Each completed execution node should also create a standalone HTML note under
`project_tracking/updates/` and register it in `project_tracking/updates/index.json`.
The main dashboard renders these milestone links so review can happen from the
public site without opening repo markdown first.

## Source of Truth

Do not hand-edit `project_tracking/projects/hoi3r_submission.json` during normal
workflow. The dashboard data is generated from:

- `docs/NEURIPS_2026_SUBMISSION_PLAN.md`

## Regeneration

Run:

```bash
python scripts/export_project_tracking.py
bash scripts/publish_project_tracking_public.sh
```

This command updates:

- `project_tracking/projects/index.json`
- `project_tracking/projects/hoi3r_submission.json`

Then publish the refreshed static files to the public mirror repo so the GitHub
Pages site stays in sync.

## Purpose

This dashboard is a high-level overview surface for the HOI3R NeurIPS 2026
submission plan. Daily execution details remain in markdown planning docs and
Notion.
