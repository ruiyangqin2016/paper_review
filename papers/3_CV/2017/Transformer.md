# Attention Is All You Need (Transformer)

[自我复现的代码](https://github.com/ruiyangqin2016/paper_review/tree/main/Codes/3_CV/2017/transformer) <br/>
Paper: [Click to view](https://proceedings.neurips.cc/paper/2017/file/3f5ee243547dee91fbd053c1c4a845aa-Paper.pdf) <br/>
Code: https://github.com/tensorflow/tensor2tensor <br/>
Blog: https://zhuanlan.zhihu.com/p/48508221 <br/>
李沐推荐：[对Attention在Transformer里面作用的研究](https://arxiv.org/pdf/2103.03404.pdf) <br/>
论文精读：[点击观看](https://www.bilibili.com/video/BV1pu411o7BE?from=search&seid=12955223521465408259&spm_id_from=333.337.0.0)

## 1. Abstract
Traditional models are based on encoder-decoder structure. The model called **Transformer** is solely based on attention mechanism, dispensing with recurrence and convolutions entirely. 更详细的说，Transformer由且仅由self-Attenion和Feed Forward Neural Network组成。一个基于Transformer的可训练的神经网络可以通过堆叠Transformer的形式进行搭建。

相比较RNN算法，whose计算顺序只能为从右到左或者从左到右，Transformer使用Attention机制将序列中的任意两个位置之间的距离是缩小为一个常量。在论文中，Transformer的定义为：Transformer is the first transduction model relying entirely on self-attention to compute representations of its input and output without using sequence aligned RNNs or convolution。

For sequence modeling and transduction probelms such as language modelings and machine translation, estabilished methods are:
> Recurrent neural networks <br/>LSTM-Long short-term memory <br/>Gated recurrent neural networks.

Different from those architectures, **Transformer**: 
> It eschewes recurrence and relies solely on an attention mechanism. <br/>It draws global dependencies between input and output. <br/>It allows more parallelization.

## 2. Model Architecture
<img align="right" src=https://github.com/ruiyangqin2016/paper_review/blob/main/image_segmentation/pic/transformer_1.jpeg width=30%>

1. Encoder: (x<sub>1</sub>,...,x<sub>n</sub>) ---> {Encoder} ---> **z** = (z<sub>1</sub>,...,z<sub>n</sub>)
2. Decoder: Given **z**, decoder generates an output sequence (y<sub>1</sub>,...,y<sub>n</sub>), one element at a time.
3. Each step, the model is **auto-regressive**.
4. Stacked self-attention, point-wise, fully connected layers for both decoder and encoder.

### 2.1 Encoder 和 Decoder

### 2.2 Attention

### 2.3 Position-wise Feed-Forward Networks

### 2.4 Embeddings and Softmax

### 2.5 Positional Encoding
