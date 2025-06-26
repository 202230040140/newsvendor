本项目是关于"将深度学习应用于Newsvendor问题"的研究与实现。Newsvendor问题是运筹学和供应链管理中的一个经典库存优化问题，主要用于确定易腐商品（如报纸、生鲜、机票、时尚品等）的最优订货量，以在面临需求不确定性的情况下，最小化缺货和滞销带来的总成本。

---

### 项目内容简介

- **核心目标**：本项目旨在利用深度神经网络（DNN）直接学习和优化Newsvendor问题的订货决策，而不是传统方法那样先估计需求分布再优化订货量。
- **主要文件**：`rQ_dnn.py` 是主程序，包含了训练Newsvendor模型和rQ模型的全部函数。
- **数据集**：项目包含了用于实验的真实零售篮子数据（basket dataset）和用于生成模拟数据的代码。
- **方法创新**：项目提出了两种基于Newsvendor成本函数的DNN损失函数（DNN-ℓ₁和DNN-ℓ₂），使得神经网络能够直接最小化Newsvendor成本，而不是仅仅预测需求。
- **实验对比**：项目不仅实现了DNN方法，还实现了经典的SEO（分步估计与优化）、EQ（估计分位数）、KNN、核方法、随机森林（RF）、SAA等多种算法，并在真实和模拟数据集上进行了对比实验。

### 背景与意义

传统Newsvendor模型假设需求分布已知或可通过历史数据估计，但在实际中，数据有限或分布未知时，传统方法效果有限。深度学习方法则可以直接利用历史数据和特征信息（如天气、日期、门店等），无需显式建模需求分布，直接输出最优订货量，尤其在数据复杂或噪声较大时表现更优。

### 参考原论文介绍

- 该方法突破了传统模型的局限，能够在数据量小、分布未知或历史数据波动较大时依然有效。
- DNN方法通过自定义损失函数，将Newsvendor的成本结构融入神经网络训练过程，实现了端到端的最优订货决策学习。
- 实验结果显示，DNN方法在多种场景下均优于或接近最优的传统方法，尤其在数据噪声大或分布难以拟合时优势明显。

> 详细背景和方法介绍可参考原论文作者博客：[Newsvendor Problem and Deep Learning Approach](https://oroojlooy.github.io/blog/newsvendor/)

---

**简要总结**：  
本项目是一个结合深度学习与经典Newsvendor库存优化问题的研究实现，旨在通过神经网络直接学习最优订货策略，适用于实际供应链中需求分布未知或数据复杂的场景。

---

This repository includes the files for the paper of "Applying Deep Learning to the Newsvendor Problem". 
Also, the basket dataset will be included. Currently the code to generate simulated datasets is included.  

The main file to run is `rQ_dnn.py`, which includes all the functions to train both the newsvendor and rQ model.

---

## 相关论文详细介绍

### A Deep Learning Approach to the Newsvendor Problem (arXiv:1607.02177)

本项目对应的核心论文是 "A Deep Learning Approach to the Newsvendor Problem"（作者：Amin Oroojlooyjadid, Lawrence V. Snyder, Martin T. Takáč, and Darla M. Castelli），该论文首次将深度学习方法系统性地应用于经典Newsvendor库存优化问题。

#### 1. 研究背景
Newsvendor问题是供应链管理中的经典问题，目标是在需求不确定的情况下，确定最优订货量以最小化缺货和滞销的总成本。传统方法通常假设需求分布已知或可通过历史数据估计，但在实际应用中，需求分布往往未知或难以准确拟合。

#### 2. 主要贡献
- 创新性地将深度神经网络（DNN）用于Newsvendor问题，直接从历史数据和特征中学习最优订货策略，无需显式建模需求分布。
- 提出了两种新的损失函数，分别基于Newsvendor的成本结构（shortage cost 和 holding cost），使得神经网络能够直接最小化Newsvendor的期望成本，而不是仅仅预测需求。
- 系统性地与多种传统和机器学习方法对比，包括SEO（Separated Estimation and Optimization）、EQ（Estimated Quantile）、KNN、核方法、随机森林（RF）、SAA等。

#### 3. 方法细节
- **模型结构**：采用多层前馈神经网络，将历史特征（如天气、日期、门店等）作为输入，输出为最优订货量。
- **损失函数设计**：
  - DNN-ℓ₁损失：直接对应Newsvendor的线性成本结构。
  - DNN-ℓ₂损失：考虑了成本的平方项，适用于某些实际场景。
- **训练方式**：通过反向传播和梯度下降等常规深度学习方法进行训练。

#### 4. 实验与结果
- **数据集**：包括真实零售数据（如篮子数据集）和多种模拟数据集。
- **对比方法**：与传统SEO、EQ、KNN、RF等方法在多种场景下进行对比。
- **结果分析**：
  - DNN方法在数据量大、特征复杂或需求分布未知/难以拟合时表现优异。
  - 在数据噪声较大或历史数据有限的情况下，DNN方法依然能够获得接近最优甚至优于传统方法的订货策略。
  - DNN方法无需显式估计需求分布，适应性更强，泛化能力更好。

#### 5. 结论与展望
- 论文证明了深度学习方法在Newsvendor问题上的有效性和优越性，尤其适用于实际供应链中数据复杂、分布未知的场景。
- 该方法为后续将深度学习应用于更复杂供应链优化问题（如多级库存、动态定价等）提供了理论和实践基础。

**原文链接**：[A Deep Learning Approach to the Newsvendor Problem (arXiv:1607.02177)](https://arxiv.org/pdf/1607.02177)

