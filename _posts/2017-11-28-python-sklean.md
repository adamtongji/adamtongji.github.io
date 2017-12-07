---
layout: post
title: Scikit-learin学习
categories: [python, 机器学习]
description: 万门sklearn笔记
keywords: sklearn, python
---

**主要分类**
1. clustering
2. classification
3. regression
4. dimension reduction

**ML流程**
1. 获取数据，下载raw data
2. 清洗数据, 去noise，正则化，标准化
3. 拿数据去训练模型
4. 测试数据集
5. 提升算法准确度

```
%matplotlib inline # ipython图形在网页中展示
```

#### Esitmator框架
```{python}
model=EstimotorObject() # 实例化一个model，比如svm,RF
model.fit(dataset.data,dataset.target) #拟合这个数据集
model.predict(dataset.data) # 在测试数据集预测
model.transfrom(dataset.data) # 非监督学习
# 举例
from sklearn.linear_model import LinearRegression
model=LinearRegression()

```
#### 监督学习
```{python}
model.predict()
model.predict_proba() # 属于每个类别的概率
model.score() # 模型效果

```
#### 非监督学习
```
model.transform()
model.fit_transfrom() # 一步fit和predict。
```