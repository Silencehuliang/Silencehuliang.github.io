# 机器学习学习笔记


## 机器学习

### 概念：

- 机器学习是一门人工智能的科学，该领域的主要研究对象是人工智能，特别是如何在经验学习中改善具体算法的性能。

- 机器学习是对能通过经验自动改进的计算机算法的研究。

- 机器学习是用数据或以往的经验，以此优化计算机程序的性能标准。

（官方语言来自维基百科）

简单理解就是通过让机器学习相关算法，拥有预测的能力，然后做出相关操作。机器学习的本质就是通过给机器数据，让机器在数据中寻找相关关系

**简单的理解人工智能包括了机器学习算法、搜索算法等，深度学习又是机器学习的一种延伸。**

### 数据

数据集:一种由数据所组成的集合，一般数据含有集有特征与标签，每一行的数据表示为一个样本，每一列的数据（除最后一列外）表示为一个特征，最后一列的数据表示为标签。在具体的算法中数据集包括训练集与测试集。利用数据集可视化可以生产特征空间，根据特征的维度可以生产高维的特征空间。

### 流程

通用流程：

学习数据-->机器学习算法-->模型-->输入样例-->输出结果

### 预测结果

#### 分类

##### 分类、回归

- 根据机器学习的流程来选择两类任务
  - 分类：当希望机器学习可以预测类别的时候
    - 常见的分类方式：二分类、多分类
  - 回归：希望机器学习可以预测连续数字的值
    - 可以将回归任务简化为分类任务

##### 有无监督

监督学习、非监督学习、半监督学习、增强学习

- 监督学习：给机器的训练数据拥有标记
  - 常见的监督学习：K近邻（KNN）、线性回归、多项式回归、逻辑回归、SVM、决策树、随机森林
- 非监督学习：给机器的训练数据没有任何“标记”
	- 常见的非监督学习：聚类分析、对数据进行降维处理，数据集的特征提取提取

- 半监督学习：给机器的训练数据一部分数据有标记，另一部分没有
  - 造成数据缺失的原因：各种原因产生的样本或者标记缺失
  - 半监督学习在平时比较常见，大多都需要我们在处理数据，再交给机器进行学习

- 增强学习：根据周五的环境采取行动，根据采取行动的结果，学习行动方式

  - 以监督学习和半监督学习为基础

    
##### 学习环境

批量学习、在线学习

- 批量学习：在训练模型时，一次性的把所有样本全部输入

  - 优点：简单，写好一个算法就不更改与完善

  - 缺点：不能适应环境的变化、想适应变化需要重新批量学习

- 在线学习：在训练模型时，每输入一个样本都会计算下误差，调整一下参数

  - 优点：及时反映新的环境变化

  - 缺点：新的数据可能带来的不良变化

##### 学习方式

参数学习、非参数学习

- 参数学习：基于数据，假设关系，找到关系参数

  - 特点：通过数据集学习，学习到参数，当学习到参数时，就不再需要原有数据集

- 非参数学习：不对模型进行过多假设
  - 注意：非参数不等于没参数
