# A Simple Framework for Contrastive Learning of Visual Representations

Paper: http://proceedings.mlr.press/v119/chen20j.html

## 2. Method
SimCLR这个框架学习representations，通过maximizing agreement,在相同数据的不同增强结果(augmented view),用contrastive loss function得出。
### 2.1 对比学习框架
- Stochastic data augmentation:将一张图片随即进行两种不同的处理，处理结果分别记作 x˜i 和 x˜j
  - Random cropping
  - Random color distortions
  - Random Gaussian blur <br/>
 （Random crop + color distortion的组合一般可以取得很好的效果）
- Neural network base encode f(·):从x˜i 和 x˜j中提取向量。f(·)可以是很多框架，在这里作者选用了ResNet。hi = f(x˜i) = ResNet(x˜i) where hi ∈ R d is the output after the average pooling layer.
- Neural Network projection head **g(·)**：<br/>
  1. Representation -> g(·) -> |--Contrastive Loss--|
  2. g(·) = MLP(Multi-Layer Perception) + a hidden layer
  3. z<sub>i</sub> = g(h<sub>i</sub>) = W<sup>(2)</sup>σ(W<sup>(1)</sup>h<sub>i</sub>) <br/>
  （σ is a ReLU nonlinearity）
- Contrastive loss function: 计算z<sub>i</sub>到z<sub>j</sub>的距离。（Contrastive loss takes the output of the network for a positive example and calculates its distance to an example of the same class and contrasts that with the distance to negative examples. ）

## Notes
### 
