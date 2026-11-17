# 011：Paddy竞赛进阶技巧 🚀

![](img/b9abccdfbedad987b10601da82fddb62_1.png)

在本节课中，我们将学习如何系统地进行模型实验、跟踪结果并优化Kaggle竞赛提交。我们将涵盖从基础实验设置到高级集成策略的完整流程。

---

## 概述

![](img/b9abccdfbedad987b10601da82fddb62_3.png)

![](img/b9abccdfbedad987b10601da82fddb62_5.png)

上一节我们介绍了Kaggle竞赛的基础知识。本节中，我们将深入探讨如何通过系统化的实验、结果分析和模型集成来提升竞赛成绩。我们将学习使用工具跟踪实验、分析超参数影响，并最终构建一个强大的集成模型。

![](img/b9abccdfbedad987b10601da82fddb62_7.png)

![](img/b9abccdfbedad987b10601da82fddb62_9.png)

---

![](img/b9abccdfbedad987b10601da82fddb62_11.png)

![](img/b9abccdfbedad987b10601da82fddb62_13.png)

## 实验设置与跟踪

![](img/b9abccdfbedad987b10601da82fddb62_15.png)

![](img/b9abccdfbedad987b10601da82fddb62_17.png)

![](img/b9abccdfbedad987b10601da82fddb62_19.png)

为了高效地进行模型实验，我们需要一个系统来跟踪不同的配置和结果。以下是设置实验跟踪的关键步骤。

![](img/b9abccdfbedad987b10601da82fddb62_21.png)

![](img/b9abccdfbedad987b10601da82fddb62_23.png)

### 使用脚本进行批量训练

![](img/b9abccdfbedad987b10601da82fddb62_25.png)

将笔记本中的训练代码重构为独立的Python脚本，便于批量运行和参数化。例如，一个基础的训练脚本可能如下所示：

![](img/b9abccdfbedad987b10601da82fddb62_27.png)

![](img/b9abccdfbedad987b10601da82fddb62_29.png)


![](img/b9abccdfbedad987b10601da82fddb62_31.png)

```python
import argparse
from fastai.vision.all import *
def train(data_path, model_name, lr=0.008):
    # 1. 加载数据
    dls = ImageDataLoaders.from_folder(...)
    # 2. 创建学习器
    learn = vision_learner(dls, model_name, metrics=error_rate)
    # 3. 训练模型
    learn.fine_tune(epochs, lr)
    # 4. 记录结果（例如，使用wandb）
    return learn
```

![](img/b9abccdfbedad987b10601da82fddb62_33.png)

### 利用Weights & Biases进行实验管理

![](img/b9abccdfbedad987b10601da82fddb62_35.png)

![](img/b9abccdfbedad987b10601da82fddb62_37.png)

Weights & Biases（wandb）是一个强大的实验跟踪平台。它可以自动记录超参数、指标、系统资源使用情况，并与Git提交关联。

*   **创建扫描（Sweep）**：通过一个YAML配置文件定义要探索的超参数网格。
*   **并行运行**：在多个GPU上同时启动多个实验运行。
*   **结果分析**：通过API获取所有运行结果，并转换为Pandas DataFrame进行灵活分析。

![](img/b9abccdfbedad987b10601da82fddb62_39.png)

![](img/b9abccdfbedad987b10601da82fddb62_41.png)

```python
import wandb
api = wandb.Api()
sweep = api.sweep("project/sweep_id")
runs_df = pd.DataFrame([r.config for r in sweep.runs])
```

---

![](img/b9abccdfbedad987b10601da82fddb62_43.png)

![](img/b9abccdfbedad987b10601da82fddb62_44.png)

## 超参数探索策略

在探索超参数时，采用系统化的策略比盲目的网格搜索更有效。

### 假设驱动的实验

与其运行庞大的超参数网格搜索，不如基于假设进行测试。例如：
*   假设：不同架构的最佳学习率是相似的。
*   测试方法：用几种代表性架构（如CNN、Transformer）在固定数据集上测试少量学习率。
*   结论：如果发现0.008对大多数模型都表现良好，后续实验就可以固定此值，从而减少搜索维度。

![](img/b9abccdfbedad987b10601da82fddb62_46.png)

![](img/b9abccdfbedad987b10601da82fddb62_48.png)

![](img/b9abccdfbedad987b10601da82fddb62_50.png)

### 关键发现

通过系统实验，我们常能发现一些通用规律：
*   **学习率**：对于计算机视觉任务，一个较优的学习率（如0.008）通常在多种架构和数据集上表现稳定。
*   **图像调整方法**：对于大多数模型，“裁剪”（crop）方法通常优于“挤压”（squish）。但对于ViT等固定输入尺寸的模型，“填充”（pad）可能是更好的选择。
*   **模型选择**：在Paddy竞赛中，Vision Transformer（ViT）模型明显优于其他卷积网络模型。

---

![](img/b9abccdfbedad987b10601da82fddb62_52.png)

## 模型集成与提交优化

单一模型的表现存在上限，集成多个模型可以显著提升预测的鲁棒性和准确性。

![](img/b9abccdfbedad987b10601da82fddb62_54.png)

![](img/b9abccdfbedad987b10601da82fddb62_55.png)

### 集成方法

![](img/b9abccdfbedad987b10601da82fddb62_57.png)

1.  **选择基模型**：根据实验，挑选出几个表现最佳且差异化的模型（例如，最好的ViT模型和最好的ConvNeXt模型）。
2.  **生成预测**：用每个模型对测试集进行预测（通常使用测试时增强TTA）。
3.  **组合预测**：对多个模型的预测概率进行平均（或加权平均）。

![](img/b9abccdfbedad987b10601da82fddb62_59.png)

```python
# 假设 preds_vit, preds_convnext 是形状为 [n_samples, n_classes] 的概率矩阵
ensemble_preds = (preds_vit + preds_convnext) / 2
final_predictions = ensemble_preds.argmax(dim=1) # 获取最终类别
```

![](img/b9abccdfbedad987b10601da82fddb62_61.png)

### 提交策略

![](img/b9abccdfbedad987b10601da82fddb62_63.png)

![](img/b9abccdfbedad987b10601da82fddb62_65.png)

*   **记录关联**：在Kaggle提交描述中，明确记录使用的笔记本名称和模型组合，便于回溯。
*   **渐进优化**：先提交单个最佳模型的结果作为基线，然后提交集成模型的结果，以量化集成带来的提升。

![](img/b9abccdfbedad987b10601da82fddb62_67.png)

---

## 实用工具与技巧

以下是一些能提升工作效率的Linux和开发技巧。

### 进程与作业管理

在终端中管理长时间运行的任务：
*   `Ctrl+Z`：暂停当前前台任务。
*   `jobs`：查看当前会话中的作业列表。
*   `bg %1`：将1号作业置于后台继续运行。
*   `fg %1`：将1号作业调回前台。
*   `command &`：直接在后台运行命令。

### 查找进程

查找特定的运行进程（如Jupyter）：
```bash
ps aux | grep jupyter
```

---

## 总结

![](img/b9abccdfbedad987b10601da82fddb62_69.png)

![](img/b9abccdfbedad987b10601da82fddb62_71.png)

本节课中我们一起学习了系统化进行深度学习实验的完整流程。我们从设置可跟踪的实验脚本开始，探讨了高效的超参数探索策略，并实践了通过模型集成来优化竞赛成绩的方法。关键要点在于：通过假设驱动的小规模实验发现通用规律，利用工具自动化管理实验，并最终通过集成强大且多样的模型来获得最佳表现。记住，成为优秀实践者的路径在于深入理解每个决策背后的原因，而不仅仅是运行大量实验。