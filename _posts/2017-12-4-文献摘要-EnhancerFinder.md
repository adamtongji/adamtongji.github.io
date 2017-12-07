---
layout: post
title: 文献阅读摘要: EnhancerFinder
categories: [文献阅读, 机器学习]
description: 
keywords: 文献阅读，Enhancer tagert
---

#### Paper: 2016 NG, Enhancer–promoter interactions are encoded by complex genomic signatures on looping chromatin
1. 通过HiC找到所有Interaction pairs, 作为positive。用类似距离的random regions作为negative。  
2. 单个feature分不开positive 和negative。poll2等在两个set有差异（figure1-2)  
3. 所有feature用ensembl learning（复合学习）加boosting可以很好分开  
4. 通过tree里权重，挑出最重要的features，是特定cell line中主要的区分marker。  
5. 通过enhancer和promoter，找出对应蛋白  

