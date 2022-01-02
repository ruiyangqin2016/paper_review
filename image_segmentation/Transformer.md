# Attention Is All You Need (Transformer)

Paper: https://proceedings.neurips.cc/paper/2017/file/3f5ee243547dee91fbd053c1c4a845aa-Paper.pdf <br/>
Blog: https://zhuanlan.zhihu.com/p/48508221

## Abstract
Traditional models are based on encoder-decoder structure. The model called **Transformer** is solely based on attention mechanism, dispensing with recurrence and convolutions entirely. 更详细的说，Transformer由且仅由self-Attenion和Feed Forward Neural Network组成。一个基于Transformer的可训练的神经网络可以通过堆叠Transformer的形式进行搭建。

相比较RNN算法，whose计算顺序只能为从右到左或者从左到右，Transformer使用Attention机制将序列中的任意两个位置之间的距离是缩小为一个常量。在论文中，Transformer的定义为：Transformer is the first transduction model relying entirely on self-attention to compute representations of its input and output without using sequence aligned RNNs or convolution。
