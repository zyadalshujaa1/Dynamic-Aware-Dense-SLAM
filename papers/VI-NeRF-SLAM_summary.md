# Paper 3: VI-NeRF-SLAM (2023)

[Download PDF](papers/VI-NeRF-SLAM.pdf)

## Core Problem

Traditional visual SLAM systems using sparse point clouds struggle with:
- Scene occlusions  
- Low-density maps insufficient for high-level robotic tasks  

NeRF-based SLAM offers dense reconstructions but has limitations:
- Heavy reliance on RGB-D sensors  
- Slow convergence speeds  
- Dependence on large pre-trained networks (e.g., Droid-SLAM)  
These limitations prevent **real-time, pre-training-free deployment** in novel environments.

## Key Technical Idea and Pipeline

- **Front-end Perception (Deep Learning):** SuperPoint + LightGlue for feature extraction and matching  
- **Tracking & State Estimation (Classical SLAM):** Rule-based optimization (Ceres) minimizes reprojection error and IMU residuals for fast camera poses and sparse depth  
- **Mapping (NeRF Back-end):** Sparse depths supervise multi-resolution hash-encoded NeRF via Tiny-MLP for color and density  
- **Loop Closure:** Spatiotemporal transformations remap previous NeRF parameters to updated global frame  
- **IMU Compensation:** Dynamic noise covariance inflation handles rapid motion

## Experimental Setup & Results

- **Datasets:** Euroc (grayscale + IMU), Replica (RGB indoor)  
- **Metrics:** ATE for tracking, PSNR for photometric accuracy, Depth L1 loss for geometric accuracy  
- **Results:**  
  - Tracking: ATE significantly lower than NeRF-SLAM and Orbeez-SLAM (e.g., 0.037 cm)  
  - Efficiency: 25–26 FPS (real-time)  
  - Robustness: IMU compensation prevents tracking loss in high-motion environments

## Limitations & Implicit Assumptions

- Exhibits **artifacts in grayscale reconstructions**  
- Does not handle **dynamic objects**  
- Designed for **bounded indoor environments**, struggles with unbounded outdoor scenes  
- Relies on **geometric feature points**, fails in textureless regions

## Open Gaps

- No **semantic understanding** beyond geometric completion  
- Occupancy grid conversion for robotic navigation not implemented  
- High-end GPU required; performance on embedded platforms untested

## Insights for Future Work

- **Reusable Components:** Spatiotemporal loop closure adjustment to reuse converged NeRF weights  
- **Promising Ideas:** IMU dynamic noise inflation improves tracking under high motion  
- **Underexplored:** Using semi-dense or line-based features to improve reconstruction in low-texture areas
