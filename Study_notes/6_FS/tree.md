三种常用的思路：
  - **Filter Methods**:<br/> 过滤式方法先对数据集进行特征选择，然后再训练模型，特征选择过程与后续模型训练无关 <br/>Relief（Relevant Features）是一种著名的过滤式特征选择方法，该方法设计了一个“相关统计量”来度量特征的重要性。该统计量是一个向量，其每个分量分别对应于一个初始特征，而特征子集的重要性则是由子集中每个特征所对应的相关统计量分量之和来决定。<br/>对每个实例x，在x的同类样本中寻找最近邻，称为“猜中近邻”（near-hit）。在x的异类样本中寻找其最近邻，称为“猜错近邻”（near-miss）
    - Pearson相关系数
    - 卡方验证
    - 互信息和最大信息系数
    - 距离相关系数
    - 方差选择法
  - **Wrapper Methods**:<br/> 与过滤式特征选择不考虑后续学习器不同，包裹式特征选择直接把最终将要使用的模型的性能作为特征子集的评价标准，也就是说，包裹式特征选择的目的就是为给定的模型选择最有利于其性能的特征子集 <br/> 从最终模型的性能来看，包裹式特征选择比过滤式特征选择更好，但需要多次训练模型，因此计算开销较大 <br/> LVM（Las Vegas Wrapper）是一个典型的包裹式特征选择方法。它在拉斯维加斯方法框架下使用随机策略来进行子集搜索，并以最终分类器的误差为特征子集评价标准。LVW的计算开销很大，需要设置停止条件控制参数。
    - Random Forest
    - SVM
    - kNN
  - Embedded Methods