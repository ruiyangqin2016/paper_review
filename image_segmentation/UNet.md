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
