# Paper 1: DynaSLAM II (2020)

[Download PDF](papers/DynaSLAM_II.pdf)

## Core Problem

DynaSLAM II addresses the limitation of **static world assumptions** in classical visual SLAM systems. Most SLAM frameworks treat dynamic objects as outliers, ignoring their motion. In real-world robotics, especially in human-populated environments, ignoring dynamic objects can lead to localization errors and unsafe navigation. The paper integrates ego-motion estimation with multi-object tracking (MOT) to improve both camera localization and dynamic scene understanding.

## Key Technical Idea and Pipeline

- **Deep Learning Introduction:** Pixel-wise semantic segmentation (Mask R-CNN / YOLACT) identifies dynamic object classes (cars, pedestrians).  
- **Feature Processing:** ORB features are extracted and categorized as static or dynamic.  
- **Data Association:** Dynamic features are matched across frames using instance-level tracking (Munkres algorithm) with a constant velocity prior.  
- **Object-Centric BA:** Instead of optimizing every point, the system optimizes **6-DoF object poses** in a sliding window, reducing Hessian complexity.  
- **Joint Optimization:** Bundle Adjustment simultaneously optimizes camera poses, static map points, and dynamic
