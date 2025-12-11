# PURF

A lightweight, open-source reimplementation aligned with the RA-L paper (Density-aware Point Cloud Upsampling via Relational Graph FlowMatching). It keeps the core ideas: **density-aware heterogeneous graphs** (dense/sparse relations via a learnable threshold) and **flow-matching velocity prediction** to bridge noisy/sparse inputs to clean geometry efficiently.

## What you get (paper-matching)
- Relational graph encoder with learnable density threshold (binarized per-point density as in the paper).
- Flow-matching velocity field that maps sparse/noisy inputs to clean targets.

## File layout
```
PURF/
├─ README.md
├─ requirements.txt
├─ datasets/
│  ├─ PUGAN
│  ├─ PU1K
│  ├─ KITTI
│  └─ CAMPUS
└─ purf/
   ├─ __init__.py
   ├─ data.py            # PairedPointClouds dataset (<name>_input.xyz + <name>_gt.xyz)
   ├─ model.py           # PURFModel (hetero graph encoder + flow matching decoder)
   ├─ train.py           # CLI training script
   ├─ infer.py           # CLI inference script
   ├─ utils.py           # xyz I/O helpers
   └─ modules/
      ├─ density.py      # density estimator + learnable threshold
      ├─ graph.py        # hetero graph builder + relational conv
      └─ flow.py         # positional encoding + Chamfer + interpolation helper
```
