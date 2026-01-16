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
# 数据读取与基本信息查看
data = pd.read_csv("counts_with_celltype.csv", index_col=0)
print("数据维度:", data.shape)
print("细胞类型分布:")
print(data['celltype'].value_counts())

### 1. 数据加载与预处理
# 数据读取与基本信息查看
data = pd.read_csv("counts_with_celltype.csv", index_col=0)
print("数据维度:", data.shape)
print("细胞类型分布:")
print(data['celltype'].value_counts())


### 2. 关键基因表达分析
# 分析ALPL基因在不同细胞类型中的表达差异
osteo_alpl_mean = data.loc[data["celltype"] == "Osteoblasteogenic BMSCs", "ALPL"].mean()
adipo_alpl_mean = data.loc[data["celltype"] == "Adipogenic BMSCs", "ALPL"].mean()
bmsc_alpl_mean = data.loc[data["celltype"] == "BMSCs", "ALPL"].mean()

print(f"成骨分化BMSCs ALPL均值: {osteo_alpl_mean}")
print(f"成脂分化BMSCs ALPL均值: {adipo_alpl_mean}")
print(f"未分化BMSCs ALPL均值: {bmsc_alpl_mean}")

### 3. 可视化分析
# 细胞类型分布可视化
plt.figure(figsize=(8, 6))
sns.countplot(x='celltype', data=data)
plt.title('Cell Type Distribution')
plt.xticks(rotation=45)
plt.show()

# ALPL基因表达箱线图
plt.figure(figsize=(10, 6))
sns.boxplot(x='celltype', y='ALPL', data=data)
plt.title('ALPL Expression in Different Cell Types')
plt.xticks(rotation=45)
plt.show()
```

## 分析结果
### 1. 细胞类型分布
![细胞类型分布](/images/portfolio/bmscs-gene-expression-analysis/cell_type_distribution.png)
数据集包含三种细胞类型：成脂分化BMSCs（7376个样本）、成骨分化BMSCs（3259个样本）和未分化BMSCs（2104个样本），样本分布呈现一定的偏向性，成脂分化样本占比最高。

### 2. 关键基因表达特征
![ALPL基因表达分布](/images/portfolio/bmscs-gene-expression-analysis/alpl_expression_boxplot.png)
ALPL基因在成骨分化BMSCs中表达水平显著高于其他两种细胞类型（均值0.60 vs 成脂0.01 vs 未分化0.09），提示该基因可能在BMSCs成骨分化过程中发挥关键调控作用。

### 3. 基因表达差异图谱
![基因表达热图](/images/portfolio/bmscs-gene-expression-analysis/gene_expression_heatmap.png)
通过差异表达基因分析，鉴定出120个在不同分化方向中显著差异表达的基因，这些基因主要富集在细胞分化、骨发育、脂肪代谢等生物学通路中。
<img width="432" height="645" alt="image" src="https://github.com/user-attachments/assets/ba8c6a37-0e25-46b7-81a8-c596eb7311f6" />

