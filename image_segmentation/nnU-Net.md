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
    - [Batch normalization](https://arxiv.org/pdf/1502.03167.pdf) -> [instance normalization](https://arxiv.org/pdf/1607.08022.pdf):
      - CT: 通过统计整个数据集中mask内像素的HU值范围，clip出[0.05,99.5]百分比范围的HU值范围，然后使用z-score方法进行归一化.
      - MR: 对每个患者数据单独执行z-score归一化.
  - Pre-processing:
    - Cropping: 只在非零区域crop，减少计算消耗
    - Resample: 数据集中存在不同spacing的数据，默认自动归一化到数据集所有数据spacing的中值spacing。原始数据使用三阶spline插值；Mask使用最邻近插值。
      - UNet Cascade resample strategy: 中值尺寸大于显存限制下可处理尺寸的4倍时（batch-size=2），采用级联策略，对数据进行下采样（采样2的倍数，直到满足前面的要求）；如果数据分辨率三个轴方向不相等，先降采样高分辨率轴使得三轴相等，再三轴同时降采样直到满足上述要求。
  - What to train：
    - 2D U-Net:
      - Suboptimal, since valueable information along the z-axis cannot be aggregated and taken into consideration
      - 3D methods is deteriorate is the dataset is anisotropic [[Evidence](https://arxiv.org/abs/1707.00587)]
    - 3D full resolution U-Net：
      - The training is challenging for big datasets such as Prostate, because the limited field of view of the architecture which thus cannot collect sufficient contextual information
    - U-Net Cascade:
      - 3D low resolution U-Net
      - 3D full resolution U-Net <br/>
    <img src=https://github.com/ruiyangqin2016/paper_review/blob/main/image_segmentation/pic/nnunet_1.png width=70%>
  - Identifying the best U-Net configuration
  - Run inference:
    - Patch采样: 为了增加网络的稳定性，patch采样的时候会保证一个batch的样本中有超过1/3的像素是前景类的像素。这个很关键，否则你的前景dice会收敛的很慢。
    - Inference:
      - 所有的推理都是基于patch的。
      - patch的边界上精度会有损，因此在对patch重叠处的像素进行fuse时，边界的像素权重低，中心的像素权重高；patch重叠的stride为size/2；使用test-data-augmentation（增广方式：绕各个轴的镜像增广）；使用了5个训练的模型集成进行推理（5个模型是通过5折交叉验证产生的5个模型）
