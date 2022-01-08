# nnU-Net: Self-adapting Framework for U-Net-Based Medical Image Segmentation

Paper: [Click to view](https://arxiv.org/pdf/1809.10486.pdf) <br/>
Code: https://github.com/MIC-DKFZ/nnUNet <br/>
Zhihu: https://zhuanlan.zhihu.com/p/100014604 <br/>

## 1. Abstract
  - Adaption:
    - **Pre-processing**: resampling, normalization
    - **Training**: loss, optimizer, data augmentation
    - **Inference**: path-based strategy, test-time-augmentations
    - **Post-processing**: 增强连接
  - “nnU-Net” -> "no-new-UNet":
    - A robust and self-adapting framework
    - 2D and 3D vanilla U-Net
## 2. nnU-Net结构详解 
  - Pre-processing:
    - 
  - What to train：
    - 2D U-Net
    - 3D full resolution U-Net
    - Cascade:
      - 3D low resolution U-Net
      - 3D full resolution U-Net
  - Identifying the best U-Net configuration
