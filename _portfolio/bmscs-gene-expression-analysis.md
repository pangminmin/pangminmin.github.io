---
title: "骨髓间充质干细胞分化相关基因表达数据分析"
collection: portfolio
type: "Data Analysis"
permalink: /portfolio/bmscs-gene-expression-analysis
date: 2026-01-15
excerpt: "通过单细胞基因表达数据，系统分析骨髓间充质干细胞（BMSCs）不同分化方向的分子特征，为干细胞定向分化机制研究提供数据支撑"
header:
  teaser: /images/portfolio/bmscs-gene-expression-analysis/cell_type_distribution.png
tags:
  - 干细胞研究
  - 基因表达分析
  - 生物信息学
tech_stack:
  - name: Python
  - name: Pandas
  - name: Matplotlib
  - name: Seaborn
---

## 项目背景
骨髓间充质干细胞（BMSCs）具有多向分化潜能，可分化为成骨细胞、脂肪细胞等多种细胞类型，在再生医学领域具有重要应用价值。本项目基于单细胞基因表达数据集，系统分析BMSCs不同分化阶段的基因表达特征，挖掘关键差异表达基因，为揭示干细胞定向分化的分子机制提供数据支持。

## 核心实现
### 1. 数据加载与预处理
```python
# 数据读取与基本信息查看
data = pd.read_csv("counts_with_celltype.csv", index_col=0)
print("数据维度:", data.shape)
print("细胞类型分布:")
print(data['celltype'].value_counts())
