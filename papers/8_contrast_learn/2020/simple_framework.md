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
