# DT10 camera0 direct-gamma vs anchor-UVZ publish assets

Eval uses the same camera0 v3.6 GT cache and clip settings as training: clip_len=13, n_max=2, full DexYCB camera0 cache.
Visualization inputs use tensors emitted by p2_eval_thfm_lora directly; no hand-root subtraction or visualization-time reanchoring is applied.
Selected visualization windows: train=20200709-subject-01/20200709_141754:3, test=20200928-subject-07/20200928_143249:1.

Video render refresh:
- RGB overlay mp4s live under `videos/*_overlay.mp4`.
- 3D playback mp4s live under `videos/*_world.mp4`.
- 3D turntable mp4s live under `videos/*_world_rotate.mp4`.
- Remote generated PNG frames because remote `ffmpeg` is unavailable; local `/opt/homebrew/bin/ffmpeg` encoded the H.264 mp4s.

Global metric refresh:
- `eval_global_metrics_summary.csv/json` adds raw MPJPE, root-aligned MPJPE, PA-MPJPE, WA-MPJPE, W-MPJPE, gamma L1/L2, root-delta/root-endpoint, and global orientation metrics.
- `eval_raw/*_global_metrics.json` contains the per-eval posthoc metric records.
- These were computed from the same `predictions.pt` files using the `a8c7737` `eval_hand_metrics.py` helper contract on matched active hands.
