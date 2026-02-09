# Paper 2: DS-SLAM (2018-2021)

[Download PDF](papers/DS-SLAM.pdf)

## Core Problem

DS-SLAM addresses the **failure of static world assumptions** in classical SLAM frameworks like ORB-SLAM2. When robots operate in highly dynamic environments, moving objects (especially humans) corrupt camera pose estimation, leading to drift or failure. Beyond localization, robots require a conceptual understanding of dynamic scenes to perform higher-level tasks safely.

## Key Technical Idea and Pipeline

- **Deep Learning Introduction:** SegNet provides pixel-wise semantic masks for dynamic classes (e.g., person) on RGB frames.  
- **Classical SLAM & Geometric Check:** ORB features are extracted, and geometric consistency is checked using Lucas-Kanade optical flow and RANSAC for Fundamental Matrix.  
- **Two-Level Outlier Rejection:**  
  - Semantic masks identify potentially dynamic objects  
  - Geometric motion consistency verifies if features are moving  
  - Entire object’s features are rejected if dynamic  
- **Mapping:** Produces dense Octo-tree maps with log-odds probabilistic updates to filter transient ghosting.  
- **Multi-threaded Architecture:** SegNet and tracking run in parallel to maintain real-time performance.

## Experimental Setup & Results

- **Datasets:** TUM RGB-D (walking – high dynamic, sitting – low dynamic), TurtleBot2 validation  
- **Metrics:** Absolute Trajectory Error (ATE), Relative Pose Error (RPE)  
- **Results:**  
  - High-dynamic scenarios: ATE reduced by up to 96.7% compared to ORB-SLAM2  
  - Maintained real-time performance (~10–12 fps)

## Limitations & Implicit Assumptions

- Assumes dynamic objects belong to **predefined semantic classes**  
- Objects treated as **entirely static or moving** – struggles with articulated/deformable objects  
- Sensitive to **segmentation quality**; poor masks cause incomplete maps

## Open Gaps

- Loop closure requires **rebuilding OctoMap**, which is computationally heavy  
- Does not estimate **velocity or trajectories** of dynamic agents  
- Relies on RGB-D; limited applicability in outdoor or high-glare environments

## Insights for Future Work

- **Reusable Components:** Parallelized architecture separating segmentation from tracking, log-odds filtering in OctoMaps  
- **Promising Ideas:** Combining semantic priors with geometric evidence to determine motion  
- **Underexplored:** Expanding object classes, integrating semantic understanding into high-level navigation tasks
