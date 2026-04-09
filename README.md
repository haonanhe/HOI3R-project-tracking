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

## Lightweight Publish

For urgent pages that do not need a full mirror refresh, the publish script also
supports newline-delimited subset publishing via `PUBLISH_PATHS`:

```bash
PUBLISH_KEEP_EXISTING=1 \
PUBLISH_PATHS=$'weekly-update-2026w13' \
bash scripts/publish_project_tracking_public.sh
```

With `PUBLISH_KEEP_EXISTING=1`, the script preserves unselected remote files and
only replaces the requested paths, which is suitable for a single page refresh.
Without that flag, subset mode wipes the mirror checkout before copying only the
selected paths, so include every surface that the published homepage links to in
the same run.

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

## H2O3D Official Visual Compare Publication

Sync the generated static compare artifact into the public site subtree:

```bash
python3 scripts/sync_h2o3d_official_compare_to_project_tracking.py \
  --source-dir docs/artifacts/h2o3d_official_visual_compare_20260322_v2 \
  --output-dir project_tracking/h2o3d-official-visual-compare
```

This writes:

- `project_tracking/h2o3d-official-visual-compare/index.html`
- `project_tracking/h2o3d-official-visual-compare/report_manifest.json`
- `project_tracking/h2o3d-official-visual-compare/official/**`
- `project_tracking/h2o3d-official-visual-compare/reference/**`

Then publish the site mirror:

```bash
bash scripts/publish_project_tracking_public.sh
```

## HCU Final Visual Compare Publication

Generate the grouped HCU final-vs-`original_mano_reference` artifact:

```bash
conda run -n human3r python scripts/hand_camera_unified_interface/hcu_original_visual_compare.py \
  --output-dir docs/artifacts/hcu_original_visual_compare_20260323
```

Sync it into the public site subtree:

```bash
python3 scripts/sync_hcu_original_compare_to_project_tracking.py \
  --source-dir docs/artifacts/hcu_original_visual_compare_20260323 \
  --output-dir project_tracking/hcu-original-visual-compare
```

This writes:

- `project_tracking/hcu-original-visual-compare/index.html`
- `project_tracking/hcu-original-visual-compare/report_manifest.json`
- `project_tracking/hcu-original-visual-compare/images/**`

## Purpose

This dashboard is a high-level overview surface for the HOI3R NeurIPS 2026
submission plan. Daily execution details remain in markdown planning docs and
Notion.
