# STL-10数据集
## 1. 数据集简介
**发布方**：Adam Coates
**发布时间**：2011
**背景**：STL-10数据集是一个用于开发无监督特征学习、深度学习、自监督学习算法的图像识别数据集。其灵感来自CIFAR-10数据集，每个类别的标注图像数量相比CIFAR-10中的要少，但提供了大量的无标注图像来做无监督预训练，其主要的挑战是利用无标签图像来构建先验知识。
简介：STL-10的图像来自ImageNet，共有113000张96 x 96分辨率的RGB图像，其中训练集为5000张，测试集为8000张，其余100000张均为无标签图像。

## 2. 数据集详细信息
### 2.1 标注类别
共有10个类别
|id|name|
|--|--|
1
airplane
2
bird
3
car
4
cat
5
deer
6
dog
7
horse
8
monkey
9
ship
10
truck
2.2 数据量
训练集包含5000张有标注的图像，每个类别500张，图像来自ImageNet。
测试集包含8000张有标注的图像，每个类别800张，图像来自ImageNet。
无标签集包含100000张无标注的图像，除包含以上10个类别外，还包括其他类别的动物以及车辆，图像来自ImageNet。
2.3 训练流程
官方将训练集分为了10个fold，每个fold包含1000张图片。训练时应在每个fold上均训练一次，然后在测试集上评测模型性能。
2.4 可视化
[图片]
3. 数据集任务定义及介绍
3.1 图像分类
图像分类定义
图像分类是计算机视觉领域中，基于语义信息对不同图像进行分类的一种模式识别方法。
图像分类评价指标
- Accuracy：n_correct / n_total，标签预测正确的样本占所有样本的比例。
- 某个类别的Precision：TP/(TP+FP)，被预测为该类别的样本中，有多少样本是预测正确的。
- 某个类别的Recall：TP/(TP+FN)，在该类别的样本中，有多少样本是预测正确的。
     注：在上面的评价指标中，TP代表True Positive，FP代表False Positive，FN代表False Negative，n_correct代表所有预测正确的样本数量，n_total代表所有的样本数量。
3.2 无监督学习
无监督学习定义
根据类别未知(没有被标记)的训练样本解决模式识别中的各种问题，称之为无监督学习。
无监督学习常用算法
常用的无监督学习算法主要有主成分分析方法PCA，等距映射方法、局部线性嵌入方法、拉普拉斯特征映射方法、黑塞局部线性嵌入方法和局部切空间排列方法等。
无监督学习例子
无监督学习里典型例子是聚类，聚类的目的在于把相似的东西聚在一起，而我们并不关心这一类是什么。典型的聚类算法有K-means算法, K-medoids算法、CLARANS算法等。
4. 数据集文件结构解读
4.1 目录结构
STL-10 Dataset/
├── train_X.bin            #训练集图像数据
├── train_y.bin            #训练集图像标注
├── test_X.bin             #测试集图像数据
├── test_y.bin             #测试集图像数据
├── unlabeled_X.bin        #无标签图像数据
├── class_names.txt        #数据集类别名称
└── fold_indices.txt       #训练集的fold划分信息
4.2 元信息格式
- class_names.txt中存储了类别名称信息，每一行对应一个类别，具体内容如下：
airplane
bird
car
cat
deer
dog
horse
monkey
ship
truck
- fold_indices.txt中存储了训练集的fold划分信息，每一行对应一个fold所包含的1000张图像的index。index从0开始，对应train_X.bin中的图像顺序。其前三行的部分内容如下
3629 980 2693 3595 2169 817 2970 3494 1904 4503 3204 4305 1261 1199 ...
2633 4392 2850 4016 2255 3160 4632 891 3531 2671 1340 1651 3493 4439 ...
1355 3916 3348 3417 2726 3245 41 3239 313 1053 4002 3881 3328 3494 ...
...
4.3 标注格式
- 训练集、测试集以及无标签图像的数据均存储在后缀为"_X.bin"的二进制文件中，存储格式为列优先，一次一个通道 (前96 x  96的值是R通道，接下来的96X96是G通道，最后是B通道)，值在0-255之间。
- 训练集和测试集的标注存储在后缀为"_y.bin"的二进制文件中，值在1-10之间。
#读取数据脚本
import numpy as np

image_path = 'train_X.bin' #test_X.bin/unlabeled_X.bin
label_path = 'train_y.bin' #test_y.bin
with open(image_path, 'rb') as f:
    images = np.fromfile(f, dtype=np.uint8)
    images = images.reshape(-1, 3, 96, 96).transpose(0, 3, 2, 1) 

with open(label_path , 'rb') as f:
    labels = np.fromfile(f, dtype=np.uint8)
5. 数据集标准化及可视化
5.1 原数据集格式问题
原始数据为二进制格式，需要编写脚本进行处理才能得到图像数据以及标注数据。数据不够直观，处理较为麻烦。
5.2 标准数据集下载
https://opendatalab.com/148
5.3 标准数据集可视化（v0.3）
import os
import json
import matplotlib.image as mpimg
import matplotlib.pyplot as plt
base_dir = '<Standard Data Dir>'
with open(os.path.join(base_dir, 'dataset_info.json'), 'r') as f:
    dataset_info = json.load(f)
    id2category = {category['category_id'] : category['category_name'] \
    for category in dataset_info['tasks'][0]['catalog']}

with open(os.path.join(base_dir, 'annotations/json/train.json'), 'r') as f:
    label = json.load(f)

sample = label['samples'][0]
img_path = os.path.join(base_dir, sample['media']['path'])
category_id = sample['ground_truth'][0]['category_id']
img = mpimg.imread(img_path)  
plt.xlabel(f'Category: {id2category[category_id]}')
plt.imshow(img)
plt.show()
6. 参考资料
  - 官网：https://cs.stanford.edu/~acoates/stl10/
  - 论文：Adam Coates, Honglak Lee, Andrew Y. Ng An Analysis of Single Layer Networks in Unsupervised Feature Learning AISTATS, 2011. [PDF]
  - 数据集下载：Dataset（~2.5GB）
