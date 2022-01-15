## 1. 特征提取 & 特征选择
[参考网站1](https://zhuanlan.zhihu.com/p/34450286)
[参考网站2](https://www.zhihu.com/question/19774445/answer/1968227962)
  - 定义：
    - 特征提取(Feature Extraction): Creating a subset of new features by combinations of the exsiting features.
    - 特征选择(Feature Selection): Choosing a subset of all the features.
  - Feature Extraction:
    - PCA(主成分分析): 将n维特征映射到k维上（k<n），这k维是全新的正交特征。这k维特征称为主成分，是重新构造出来的k维特征
    - LDA(线性判别分析法): 将高维的数据样本投影到最佳判别的矢量空间，保证样本数据在该空间中有最佳的可分离性。
    - MDS(多维尺度分析法): 根据样本之间的距离关系或不相似度关系在低维空间里生成对样本的一种表示。
    - ICA(独立成分分析法): 利用统计原理把数据或信号分离成统计独立的非高斯的信号源的线性组合。
    - 核主成分分析法
      - KPCA
      - KDA
    - 流型学习：
      - IsoMap
      - LLE
      - LE
  - Feature Selection
