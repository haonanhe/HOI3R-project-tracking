# Project Tracking Dashboard

This directory hosts a repo-local static dashboard adapted from the
`yubol-bobo/Project_tracking` template.

## Public URL

The public dashboard is hosted from the mirror repository:

- Site: `https://haonanhe.github.io/HOI3R-project-tracking/`
- Mirror repo: `https://github.com/haonanhe/HOI3R-project-tracking`

The mirror repository serves the contents of this `project_tracking/` directory as
the site root.

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

## HCU Round Report Regeneration (T-HCU-17A Freeze)

The HCU report surface is generated from a machine-readable artifact and must not
be hand-edited:

```bash
python3 scripts/hand_camera_unified_interface/round_report.py \
  --input project_tracking/hcu/round_report_input.json \
  --output-dir project_tracking/hcu
```

This writes:

- `project_tracking/hcu/index.html`
- `project_tracking/hcu/report_manifest.json`

## Purpose

This dashboard is a high-level overview surface for the HOI3R NeurIPS 2026
submission plan. Daily execution details remain in markdown planning docs and
Notion.
