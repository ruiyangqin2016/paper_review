# Domain Adaption

- 概念：
  - learning from scratch  即学一个CNN网络with random initialization
  - 在新的学习任务中，可以利用现有训练好的imagenet网络提取特征，去掉最后一个分类的全连接层，在classifier层之前提取4096维的特征，这些特征称为CNN code
  - 在CNN网络结构中，前面的卷积层保留更多的普遍特征 generic features（edge detectors 或者corlor blob detectors)，后面的卷积层包含更多的 task specific 特征
- 迁移学习的两种方法：
  - 利用已有的model提取特征，后面再训练分类器，比如linear svm或者softmax classifier。
  - finetune 已有的model： 即在已训练好参数的CNN结构上，利用自己的数据进行back propagation, finetune网络已有的weights.
      (可以finetune 整个CNN ,也可以保持前面的一些层的参数不变，只finetune网络的高层部分，这样做可以防止过拟合）
- 迁移学习方法的选择：
    主要取决于数据集的大小，以及与之前预训练数据集的相关性
  - 数据集很小，与预训练数据集相似: 直接提特征，提最后一层的CNN code, 训练linear 分类器
  - 数据集很小，与预训练数据集不同： 在前面的网络层中提feature,训练线性分类器
  - 数据集很大，与预训练数据相似：finetune 整个网络层
  - 数据集很大，与预训练数据不同：可以learning from scratch，也可以在预训练的model上finetune
- 一些实用的建议：
  - finetune的时候输入图片的大小不受限制，因为forward function的与输入的spatial 大小无关，只要stride能fit
  - 把需要finetune的网络层的学习率设低一点： 因为我们默认预训练的model的参数已经很好了，因此在finetune优化的时候采取小的学习率<br/>
————————————————
版权声明：本文为CSDN博主「zbxzc」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/u014568921/article/details/52056994
