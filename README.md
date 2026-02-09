# Dynamic-Aware-Dense-SLAM
Analysis and experimental proposal for dynamic-aware dense SLAM based on DynaSLAM II, DS-SLAM, and VI-NeRF-SLAM.
## Introduction

This repository presents a research-oriented analysis and experimental proposal for dynamic-aware dense visual SLAM. The project builds on insights from three recent papers:

1. **DynaSLAM II (2020)**: Object-centric Bundle Adjustment for dynamic objects.
2. **DS-SLAM (2018-2021)**: Semantic segmentation-based rejection of dynamic features for robust real-time SLAM.
3. **VI-NeRF-SLAM (2023)**: Neural Radiance Fields-based dense reconstruction with visual-inertial odometry.

Current visual SLAM systems either:
- Remove dynamic content to maintain real-time performance, or
- Densely reconstruct the environment at the cost of computational efficiency while ignoring moving objects.

**Objective**: Explore a lightweight, real-time SLAM framework that leverages dynamic motion cues while producing dense reconstructions suitable for robotic navigation.
## Problem Statement

Current visual SLAM systems either:
- Remove dynamic content to maintain real-time localization, or
- Densely reconstruct the environment at the cost of computational efficiency while ignoring moving objects.

There is still no lightweight, real-time SLAM framework that **leverages dynamic motion cues while producing dense 3D reconstructions**, suitable for robotic navigation in human-populated indoor environments.

## Hypothesis

A temporally consistent, motion-aware segmentation approach, combined with sparse-to-dense neural reconstruction, can:
- Improve localization robustness in dynamic scenes, and
- Produce denser maps that retain real-time performance.

This approach bridges the gap between:
- Real-time robustness ( DS-SLAM),
- Dynamic object understanding (DynaSLAM II), and
- Dense neural reconstruction ( VI-NeRF-SLAM).

