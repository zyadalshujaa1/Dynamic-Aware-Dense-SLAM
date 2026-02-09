## Papers Comparison Table

| Paper | Core Idea | Dynamic Handling | Reconstruction Type | Real-Time | Key Limitation / Gap | Promising Idea |
|-------|-----------|-----------------|-------------------|-----------|--------------------|----------------|
| **DynaSLAM II (2020)** | Object-centric BA for dynamic objects | Tracks moving objects | Sparse feature-based SLAM | Moderate (10–12 fps) | Assumes rigid objects, stereo/RGB-D only | Dynamic tracking improves ego-motion |
| **DS-SLAM (2018-2021)** | Semantic segmentation to reject dynamic features | Removes dynamic objects | Sparse SLAM with Octo-map | Real-time (~10–12 fps) | Limited to known semantic classes, monocular not supported | Parallel segmentation + tracking improves robustness |
| **VI-NeRF-SLAM (2023)** | Neural Radiance Field dense reconstruction | Ignores dynamic objects | Dense NeRF + VIO | Moderate (~25 fps) | Indoor only, sparse depth supervision, no dynamic handling | IMU-based motion compensation, pre-training free |
| **HI-SLAM2 (2024-2025)** | Monocular Gaussian Splatting dense SLAM | Static world only | Dense 3DGS map | Fast (22+ FPS) | Dynamic objects not handled, scale drift in extreme cases | JDSA for scale alignment, Gaussian deformation for loop closure |

---

### Insights / Open Gaps

1. **Dynamic Awareness + Dense Mapping**: None of the four papers fully integrate **dense reconstruction with dynamic motion handling** in real-time.  
2. **Monocular Dense SLAM for Robotics**: HI-SLAM2 shows fast monocular dense mapping, but lacks dynamic object support.  
3. **Semantic + Gaussian Fusion**: DS-SLAM and HI-SLAM2 suggest opportunities to fuse **semantic priors** with **Gaussian dense maps**.  
4. **Real-Time Sparse-to-Dense Approaches**: VI-NeRF-SLAM and HI-SLAM2 point toward potential **sparse-to-dense reconstruction pipelines** for efficiency.  

---

**Experimental Proposal (Summary)**

- Combine **dynamic-aware segmentation** (DynaSLAM II / DS-SLAM) with **monocular Gaussian dense mapping** (HI-SLAM2).  
- Use **sparse-to-dense neural reconstruction** as a lightweight bridge (VI-NeRF-SLAM).  
- Goal: real-time, dense, dynamic-aware SLAM suitable for indoor robotic navigation.
