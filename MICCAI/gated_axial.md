# Medical Transformer: Gated Axial-Attention for Medical Image Segmentation

Code: https://link.zhihu.com/?target=https%3A//github.com/jeya-maria-jose/Medical-Transformer<br/>
Paper: https://arxiv.org/abs/2102.10662<br/>
Zhihu: https://zhuanlan.zhihu.com/p/408662947<br/>

## Abstract
Deep conv nerual networks到目前为止被广泛应用于医学成像。However, due to inherent inductive biases(归纳偏差)， they lack understanding of long-range dependencies. 在ConvNets中，每个卷积核只关注图像的局部子集，并迫使网络关注局部模式而不是全局上下文。

理解远程依赖关系，以及其对医学图像的重要性：<br/>
>远程依赖和找局部、全局最优解有一定的关联。它们可以帮助理解。远程依赖是关于不同图像分区之间的关联。由于图像的背景是分散的，学习对应于背景的像素之间的长范围相关性可以帮助网络防止将像素误分类为掩码，减少误报。类似地，每当分割掩码较大时，了解与该掩码对应的像素之间的长期相关性也有助于做出有效的预测。

理解Transformer-based network architecture: <br/>
