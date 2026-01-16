---
title: "骨髓间充质干细胞分化相关基因表达数据分析"
collection: portfolio
type: "Data Analysis"
permalink: /portfolio/bmscs-gene-expression-analysis
date: 2026-01-10
excerpt: "通过单细胞基因表达数据，系统分析骨髓间充质干细胞（BMSCs）不同分化方向的分子特征，为干细胞定向分化机制研究提供数据支撑"
header:
  teaser: /images/portfolio/bmscs-gene-expression-analysis/特征基因在细胞类型中的平均表达量.png
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
```
### 2. 关键基因表达分析
```python
# 分析ALPL基因在不同细胞类型中的表达差异
osteo_alpl_mean = data.loc[data["celltype"] == "Osteoblasteogenic BMSCs", "ALPL"].mean()
adipo_alpl_mean = data.loc[data["celltype"] == "Adipogenic BMSCs", "ALPL"].mean()
bmsc_alpl_mean = data.loc[data["celltype"] == "BMSCs", "ALPL"].mean()
```
## 分析结果
### 1. 特征基因表达的细胞比例
![不同样本处理的细胞表达特征基因的比例](/images/portfolio/bmscs-gene-expression-analysis/不同细胞类型正表达对应基因.png)

数据集包含三种细胞类型：成脂诱导分化BMSCs（7376个样本）、成骨诱导分化BMSCs（3259个样本）和未诱导分化BMSCs（2104个样本），为判断不同的处理对BMSCs的诱导作用,分别对成脂、成骨和未分化的marker进行计算,观察不同的处理对细胞marker的影响,根据检测后的数据,ALPL在成骨诱导样本中,约40%的细胞有表达;而在成脂肪诱导样本中,表达特征基因FABP4有近60%,而其他间充质细胞marker,在各个样本中都有,但表达比例以未分化的BMSCs占比高。

### 2. 特征基因表达分布细胞分布
![成骨诱导、成脂肪诱导与未处理的BMSCs的特征基因表达分布](/images/portfolio/bmscs-gene-expression-analysis/特征基因在细胞类型中的平均表达量.png)

ALPL基因在成骨诱导的细胞类型中高表达,FABP4基因在成脂肪诱导的细胞类型中特征性高表达,而其余间充质干细胞的特征基因在这几个样本的细胞中都有表达,但表达比例存在差异，提示该不同的谱系特征基因在BMSCs分化过程中变化。

### 3. 机器学习训练效果
![混淆矩阵](/images/portfolio/bmscs-gene-expression-analysis/混淆矩阵.png)

通过对已有的数据进行训练集和测试集的划分,使用逻辑回归进行分类任务训练,用测试集进一步预测。进一步说明了经过诱导的细胞,已经发生了相应的变化,即使不是所有的细胞都表达对应的marker,但是经过机器学习,仍能通过其他特征对细胞进行分类。

### 4. 特征贡献度
![Adipogenic BMSCs——基因特征对模型预测的SHAP影响分析](/images/portfolio/bmscs-gene-expression-analysis/Adipogenic BMSCs SHAP Value.png)
![BMSCs——基因特征对模型预测的SHAP影响分析](/images/portfolio/bmscs-gene-expression-analysis/BMSCs SHAP Value.png)
![Osteoblastgenic BMSCs——基因特征对模型预测的SHAP影响分析](/images/portfolio/bmscs-gene-expression-analysis/Osteoblastgenic BMSCs SHAP Value.png)

展示了不同基因在不同处理的细胞类型对模型预测结果的影响

### 5. 特征基因SHAP依赖关系图
![Adipogenic BMSCs——SHAP 依赖关系图](/images/portfolio/bmscs-gene-expression-analysis/Dependence plots for Adipogenic BMSCs.png)
![BMSCs——SHAP 依赖关系图](/images/portfolio/bmscs-gene-expression-analysis/Dependence plots for BMSCs.png)
![Osteoblastgenic BMSCs——SHAP 依赖关系图](/images/portfolio/bmscs-gene-expression-analysis/Dependence plots for Osteoblastgenic BMSCs.png)

这组图展示了 3 个基因（FABP4、ALPL、THY1）的表达水平对不同处理的细胞类型分类预测的SHAP值影响





















