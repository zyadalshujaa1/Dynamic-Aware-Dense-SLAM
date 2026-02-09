# Dynamic-Aware-Dense SLAM

Analysis and experimental proposal for dynamic-aware dense SLAM based on **DynaSLAM II, DS-SLAM, VI-NeRF-SLAM, and HI-SLAM2**.

## Introduction

This repository presents a research-oriented analysis and experimental proposal for dynamic-aware dense visual SLAM. The project builds on insights from four recent papers:

1. **DynaSLAM II (2020)**: Object-centric Bundle Adjustment for dynamic objects.  
2. **DS-SLAM (2018-2021)**: Semantic segmentation-based rejection of dynamic features for robust real-time SLAM.  
3. **VI-NeRF-SLAM (2023)**: Neural Radiance Fields-based dense reconstruction with visual-inertial odometry.  
4. **HI-SLAM2 (2024-2025)**: Monocular Gaussian Splatting-based dense SLAM achieving high geometric accuracy and fast runtime.  

Current visual SLAM systems either:  
- Remove dynamic content to maintain real-time performance, or  
- Densely reconstruct the environment at the cost of computational efficiency while ignoring moving objects.  

**Objective**: Explore a lightweight, real-time SLAM framework that leverages **dynamic motion cues**, semantic understanding, and dense Gaussian reconstruction, suitable for robotic navigation in populated or complex indoor environments.

---

## Problem Statement

Current visual SLAM systems still face several challenges:

- **Dynamic content handling**: Systems like DS-SLAM or DynaSLAM II filter or track dynamic objects, but dense reconstruction is limited.  
- **Dense monocular mapping**: Neural or Gaussian-based methods (VI-NeRF-SLAM, HI-SLAM2) produce high-fidelity maps but often **ignore moving objects** or assume static environments.  
- **Real-time efficiency**: Combining robustness, dynamic awareness, and dense reconstruction in real time remains an unsolved problem.  

There is no existing framework that simultaneously:  
- Leverages dynamic motion cues,  
- Produces dense 3D reconstructions, and  
- Maintains real-time performance suitable for robotic navigation in human-populated environments.  

---

## Hypothesis

A temporally consistent, **motion-aware segmentation approach**, combined with **sparse-to-dense neural and Gaussian reconstruction**, can:

- Improve **localization robustness** in dynamic scenes.  
- Produce **dense, metrically accurate maps** while maintaining real-time performance.  

This approach bridges the gap between:

- **Real-time robustness** (DS-SLAM),  
- **Dynamic object understanding** (DynaSLAM II),  
- **Dense neural reconstruction** (VI-NeRF-SLAM), and  
- **High-quality monocular Gaussian SLAM** (HI-SLAM2).
