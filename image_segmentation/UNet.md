# U-Net: Convolutional Networks for Biomedical Image Segmentation

Paper: [Click to view](https://arxiv.org/pdf/1505.04597.pdf) <br/>
Code: https://github.com/milesial/Pytorch-UNet <br/>
Zhihu: https://zhuanlan.zhihu.com/p/150579454 <br/>

## 1. Abstract
  - 结构的三个特征：1. Data augmentation。2. Contracting path。3. Symmetric expanding path
  - 属于[FCN](https://github.com/ruiyangqin2016/paper_review/blob/main/CNN/FCN.md)的一种变体。除了医学图像分割，还可以应用于卫星图像分割，工业瑕疵检测等等。
  - Encoder-Decoder结构
## 2. U-net 网络结构解析
  - U-net architecture: <img src=https://github.com/ruiyangqin2016/paper_review/blob/main/image_segmentation/pic/unet_1.png width=60%>
  - 结构含义：
    - 框：feature map
    - 蓝色箭头：3x3卷积，用于特征提取
    - 灰色箭头：skip-connection，用于特征融合
    - 红色箭头：pooling(池化)，用于降低维度
    - 绿色箭头：upsample(上采样)，用于恢复纬度
    - 青色箭头：1x1卷积，用于输出结果
  - 原文重点摘抄：
    > 1. For FCN, The main idea is to supplement a usual contracting network by successive layers, where pooling operators are replaced by upsampling operators. <br/>
    > 2. In order to localize, high resolution features from the contracting path are combined with the upsampled output. <br/>
    > 3. A successive convolution layer can then learn to assemble a more precise output based on this information. <br/>
    > 4. One important modification in our architecture is that in the upsampling part we have also a large number of feature channels, which allow the network to propagate context information to higher resolution layers. As a consequence, the expansive path is more or less symmetric to the contracting path, and yields a u-shaped architecture. 

  - Network Architecture
    - Contracting Path (left), expansive path (right)
      - Contracting path: 3x3 unpadded convolution -> ReLU -> 2x2 max pooling with stride 2 for downsampling
        - Downsampling: double the number of feature channels
      - Expansive path: Upsampling feature map -> 2x2 up-convolusion -> two 3x3 convolutions each followed by ReLU
        - 2x2 convolusion: halves the number of feature channels, a concatenation with the correspondingly cropped feature map from the contracting path
        - Cropping: necessary, since loss of border pixels in every convolution.
    - Final layer: 1x1 convolution layer, map each 64-component feature vector to the disired number of classes.
    - In total: 23 layers
    - Note: FCN 中深层信息与浅层信息融合是通过对应像素相加的方式，而 Unet 是通过拼接的方式。
      - 在相加的方式下，feature map 的维度没有变化，但每个维度都包含了更多特征，对于普通的分类任务这种不需要从 feature map 复原到原始分辨率的任务来说，这是一个高效的选择；而拼接则保留了更多的维度/位置 信息，这使得后面的 layer 可以在浅层特征与深层特征自由选择，这对语义分割任务来说更有优势。
