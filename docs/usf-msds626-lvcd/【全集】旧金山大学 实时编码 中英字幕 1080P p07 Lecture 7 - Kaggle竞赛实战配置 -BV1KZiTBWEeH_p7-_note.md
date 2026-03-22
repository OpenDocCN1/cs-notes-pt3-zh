# 旧金山大学 实时编码：第7讲：Kaggle竞赛实战配置 🚀

![](img/22c5c1dc2f027d69631a0ff98f808f53_0.png)

在本节课中，我们将学习如何配置环境并开始参与一个Kaggle图像分类竞赛。我们将从安装必要的工具开始，下载竞赛数据，并运行一个基础的深度学习模型。整个过程将帮助你熟悉在Kaggle或类似平台上进行机器学习项目的基本工作流。

## 概述

我们将跟随一个社区成员分享的Kaggle竞赛（水稻病害分类）作为实践案例。课程将涵盖从环境搭建到初步模型训练的全过程，包括安装Kaggle命令行工具、认证、下载数据、数据探索以及使用fastai库构建图像分类器。

## 环境配置与数据下载

首先，我们需要在计算环境中安装Kaggle命令行工具并配置认证，以便下载竞赛数据。

### 安装Kaggle命令行工具

Kaggle不仅是一个Python库，还提供了一个命令行工具。我们使用`pip`进行安装。

```bash
pip install --user kaggle
```

安装后，命令行工具通常位于用户主目录的`.local/bin`路径下。如果该路径不在系统的环境变量`PATH`中，我们需要手动添加。

![](img/22c5c1dc2f027d69631a0ff98f808f53_2.png)

### 配置系统路径

![](img/22c5c1dc2f027d69631a0ff98f808f53_4.png)

编辑你的shell配置文件（例如`~/.bashrc`或`~/.bash_profile`），在文件末尾添加以下行：

![](img/22c5c1dc2f027d69631a0ff98f808f53_6.png)

![](img/22c5c1dc2f027d69631a0ff98f808f53_8.png)

```bash
export PATH=$HOME/.local/bin:$PATH
```

然后，执行`source`命令使更改生效，或重新打开终端。

![](img/22c5c1dc2f027d69631a0ff98f808f53_10.png)

```bash
source ~/.bashrc
```

![](img/22c5c1dc2f027d69631a0ff98f808f53_12.png)

![](img/22c5c1dc2f027d69631a0ff98f808f53_14.png)

![](img/22c5c1dc2f027d69631a0ff98f808f53_16.png)

![](img/22c5c1dc2f027d69631a0ff98f808f53_18.png)

现在，你应该可以在终端中直接运行`kaggle`命令了。

![](img/22c5c1dc2f027d69631a0ff98f808f53_20.png)

![](img/22c5c1dc2f027d69631a0ff98f808f53_22.png)

### 设置Kaggle API认证

![](img/22c5c1dc2f027d69631a0ff98f808f53_24.png)

要使用Kaggle命令行工具下载数据，需要进行API认证。

![](img/22c5c1dc2f027d69631a0ff98f808f53_26.png)

![](img/22c5c1dc2f027d69631a0ff98f808f53_28.png)

![](img/22c5c1dc2f027d69631a0ff98f808f53_30.png)

1.  登录Kaggle网站，进入你的账户设置页面。
2.  点击“Create New API Token”。这将下载一个名为`kaggle.json`的文件到你的电脑。
3.  在你的计算环境（例如Paperspace或本地机器）中，创建一个名为`.kaggle`的目录，并将`kaggle.json`文件移动到此目录。

![](img/22c5c1dc2f027d69631a0ff98f808f53_32.png)

```bash
mkdir ~/.kaggle
mv /path/to/downloaded/kaggle.json ~/.kaggle/
```

4.  为确保安全，修改该文件的权限。

```bash
chmod 600 ~/.kaggle/kaggle.json
```

### 下载竞赛数据

找到你想参与的Kaggle竞赛页面。在“Data”选项卡下，通常会提供使用命令行下载数据的指令。例如：

```bash
kaggle competitions download -c plant-pathology-2020-fgvc7
```

![](img/22c5c1dc2f027d69631a0ff98f808f53_34.png)

运行此命令前，请确保你已点击“Join Competition”加入该竞赛。下载的数据通常是一个压缩文件，使用`unzip`命令解压。

```bash
unzip -q plant-pathology-2020-fgvc7.zip
```

![](img/22c5c1dc2f027d69631a0ff98f808f53_36.png)

![](img/22c5c1dc2f027d69631a0ff98f808f53_38.png)

**关于数据存储位置的提示**：在云平台（如Paperspace）上，将数据存储在持久化目录（如`/storage`）或临时目录（如`/home`）各有利弊。持久化目录方便但可能I/O速度较慢；临时目录速度快但会话结束后数据会丢失。你可以编写一个脚本来自动化每次启动时的数据下载和解压步骤。

![](img/22c5c1dc2f027d69631a0ff98f808f53_40.png)

![](img/22c5c1dc2f027d69631a0ff98f808f53_42.png)

## 数据探索与准备

上一节我们完成了环境和数据的准备工作，本节中我们来看看数据的具体内容，并为模型训练做准备。

解压后，查看数据目录结构。

```bash
ls -la
```

通常你会看到`train.csv`、`sample_submission.csv`以及`train_images`和`test_images`文件夹。我们可以快速查看文件数量和样本。

```bash
# 查看训练图像数量
ls train_images | wc -l
# 查看某个类别下的图像数量
ls train_images/bacterial_leaf_blight | wc -l
# 查看CSV文件的前几行
head train.csv
```

在Jupyter Notebook中，我们可以更直观地探索数据。

```python
from fastai.vision.all import *
import pandas as pd

# 设置数据路径
path = Path(‘./plant-pathology-2020-fgvc7’)
# 读取训练标签CSV
df = pd.read_csv(path/‘train.csv’)
print(df.shape)
df.head()
```

使用PIL库查看一张图片。

```python
from PIL import Image
img_path = path/‘train_images’/df.iloc[0][‘image_id’]
img = Image.open(img_path)
print(img.size)
img
```

使用fastai的`get_image_files`函数可以递归获取所有图像文件的路径列表。

```python
files = get_image_files(path/‘train_images’)
len(files)
```

## 构建与训练模型

经过数据探索，我们对数据集有了基本了解。现在，我们使用fastai库快速构建一个图像分类模型。

fastai提供了便捷的API来创建数据加载器（`DataLoaders`）。由于我们的数据已经按类别存放在不同的文件夹中，可以直接使用`ImageDataLoaders.from_folder`方法。

```python
# 定义训练和验证路径
train_path = path/‘train_images’
# 使用20%的数据作为验证集
dls = ImageDataLoaders.from_folder(train_path, valid_pct=0.2, seed=42,
                                   item_tfms=Resize(224))
# 显示一个批次的数据以确认
dls.show_batch()
```

接下来，我们创建一个卷积神经网络学习器（`Learner`），并使用预训练的ResNet架构进行迁移学习。

```python
# 使用resnet18架构，并加载预训练权重
learn = vision_learner(dls, resnet18, metrics=error_rate)
# 使用1周期策略进行微调
learn.fine_tune(1)
```

训练开始后，你可以使用`nvidia-smi`命令（如果使用GPU）来监控GPU的使用情况，确保计算资源被有效利用。

```bash
# 动态监控GPU使用率（每1秒刷新）
nvidia-smi dmon
```

关键指标是`sm`（流多处理器）利用率，通常保持在50%以上表明数据读取和预处理没有成为瓶颈。如果过低，可能需要考虑将数据移至更快的存储、预先调整图像大小或减少数据增强的复杂度。

## 总结与后续步骤

本节课中我们一起学习了参与Kaggle竞赛的完整入门流程。我们从安装和配置Kaggle命令行工具开始，下载了特定竞赛的数据集，并对数据进行了初步探索。最后，我们使用fastai库构建并训练了一个基础的图像分类模型，为水稻病害图片进行分类。

这只是一个起点。在后续的学习中，你可以尝试：
*   将模型训练更多轮次以提高精度。
*   尝试不同的网络架构（如resnet34, resnet50）。
*   进行更细致的数据增强。
*   使用学习率查找器来寻找最佳学习率。
*   将训练好的模型生成预测文件，并提交到Kaggle竞赛中查看初步排名。

![](img/22c5c1dc2f027d69631a0ff98f808f53_44.png)

![](img/22c5c1dc2f027d69631a0ff98f808f53_45.png)

通过重复这些步骤或在其他数据集上实践，你将能熟练掌握机器学习项目从环境配置到模型迭代的全过程。