
experiments/README.md


# Experiments for HI-SLAM2

This folder contains all the steps required to run HI-SLAM2 experiments, including environment setup, data preparation, demo execution, and evaluation.

---

## 1. Environment Setup

Create the conda environment and install dependencies:

```bash
conda env create -f environment.yaml
conda activate hislam2
python setup.py install


Note: Make sure your GPU supports CUDA 11.8 if you are using one.


2. Pretrained Models
Download the pretrained models for depth and normal priors:
wget https://zenodo.org/records/10447888/files/omnidata_dpt_depth_v2.ckpt -P pretrained_models
wget https://zenodo.org/records/10447888/files/omnidata_dpt_normal_v2.ckpt -P pretrained_models


3. Data Preparation
Replica Dataset
Prepare the Replica dataset:
python scripts/preprocess_replica.py

Expected folder structure after preprocessing:
data/Replica/sceneXXXX/colors

ScanNet Dataset (optional)
Prepare ScanNet dataset:
python scripts/preprocess_scannet.py


Make sure to follow ScanNet download instructions for color, pose, and intrinsics. Preprocess using the script to convert the data into the expected input format.


4. Run HI-SLAM2 Demo
Run the demo on Replica data:
python demo.py \
  --imagedir data/Replica/room0/colors \
  --calib calib/replica.txt \
  --config config/replica_config.yaml \
  --output outputs/room0

Optional flags:

--gsvis : visualize Gaussian map
--droidvis : visualize intermediate point cloud


5. Evaluation
Run evaluation on all Replica sequences:
python scripts/run_replica.py

For ScanNet sequences (optional):
python scripts/run_scannet.py


6. Metrics
Metrics to compare performance:



Metric
Purpose




ATE
Absolute Trajectory Error


RPE
Relative Pose Error


PSNR
Rendering quality (dense map)


Depth L1
Geometric reconstruction accuracy


FPS
Real-time performance




7. Notes

Ensure all paths are correct before running the scripts.
Pretrained models must be in pretrained_models/ folder.
Outputs will be saved in outputs/ folder, organized per dataset sequence.
Optional visualization flags (--gsvis, --droidvis) help monitor map construction.


This file serves as the single source of truth for running experiments on HI-SLAM2 and can be directly committed to GitHub.


---
