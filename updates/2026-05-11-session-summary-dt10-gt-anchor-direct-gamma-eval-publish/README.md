# DT10 GT-anchor direct-gamma eval assets

Published assets for ACP job `pt-y1bf5vy5`. The comparison uses the same train3/test3 manifests as the 2026-05-10 camera0 direct baseline. `predictions.pt` is intentionally excluded from the public asset bundle.

Key caveat: `MANO_REPROJ_WEIGHT` was not exported for `pt-y1bf5vy5`, so weighted `mano_reproj` is zero even though `mano_reproj_unweighted` is nonzero.
