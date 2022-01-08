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
  - Replaced structures:
    - ReLU -> leaky ReLU
    - [Batch normalization](https://arxiv.org/pdf/1502.03167.pdf) -> [instance normalization](https://arxiv.org/pdf/1607.08022.pdf)
  - Pre-processing:
    - Cropping: 只在非零区域crop，减少计算消耗
    - Resample: 
  - What to train：
    - 2D U-Net:
      - Suboptimal, since valueable information along the z-axis cannot be aggregated and taken into consideration
      - 3D methods is deteriorate is the dataset is anisotropic [[Evidence](https://arxiv.org/abs/1707.00587)]
    - 3D full resolution U-Net
    - U-Net Cascade:
      - 3D low resolution U-Net
      - 3D full resolution U-Net
  - Identifying the best U-Net configuration
  - Run inference
