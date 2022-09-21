# 从手写数字识别入门深度学习丨MNIST数据集详解

MNIST数据集（Mixed National Institute of Standards and Technology database）是一个用来训练各种图像处理系统的二进制图像数据集，广泛应用于机器学习中的训练和测试。

作为一个入门级的计算机视觉数据集，发布20多年来，它已经被无数机器学习入门者“咀嚼”千万遍，是最受欢迎的深度学习数据集之一。

今天就让我们来一睹真容。

## 目录指引
1. 数据集简介
2. 数据集详细信息
3. 数据集任务定义及介绍
4. 数据集结构解读
5. 数据集下载链接


## 一、数据集简介
**发布方**：National Institute of Standards and Technology(美国国家标准技术研究所，简称NIST)

**发布时间**：1998

**背景**：
该数据集的论文想要证明在模式识别问题上，基于CNN的方法可以取代之前的基于手工特征的方法，所以作者创建了一个手写数字的数据集，以手写数字识别作为例子证明CNN在模式识别问题上的优越性。

**简介**：
MNIST数据集是从NIST的两个手写数字数据集：Special Database 3 和Special Database 1中分别取出部分图像，并经过一些图像处理后得到的。

MNIST数据集共有70000张图像，其中训练集60000张，测试集10000张。所有图像都是28×28的灰度图像，每张图像包含一个手写数字。

## 二、数据集详细信息
### 1. 数据量
训练集60000张图像，其中30000张来自NIST的Special Database 3，30000张来自NIST的Special Database 1。

测试集10000张图像，其中5000张来自NIST的Special Database 3，5000张来自NIST的Special Database 1。

### 2. 标注量
每张图像都有标注。

### 3. 标注类别
共10个类别，每个类别代表0~9之间的一个数字，每张图像只有一个类别。

### 4. 可视化
![图片1](https://mmbiz.qpic.cn/mmbiz_png/7yjDpC9UfD50Wm5degeu1n6dzUzymSe2ib6qh1Zr3kyBGfWHSocHB4AaYNQTzFWj0iaViadtBtpLyzeTdKSGylmRw/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)
图1：MNIST样例图

NIST原始的Special Database 3 数据集和Special Database 1数据集均是二值图像，MNIST从这两个数据集中取出图像后，通过图像处理方法使得每张图像都变成28×28大小的灰度图像，且手写数字在图像中居中显示。

## 三、数据集任务定义及介绍
### 1. 图像分类
**定义**
图像分类是计算机视觉领域中，基于语义信息对不同图像进行分类的一种模式识别方法。

**评价指标**

- **Accuracy**：n_correct / n_total，标签预测正确的样本占所有样本的比例。

- **某个类别的Precision**：TP/(TP+FP)，被预测为该类别的样本中，有多少样本是预测正确的。

- **某个类别的Recall**：TP/(TP+FN)，在该类别的样本中，有多少样本是预测正确的。

注：在上面的评价指标中，TP代表True Positive，FP代表False Positive，FN代表False Negative，n_correct代表所有预测正确的样本数量，n_total代表所有的样本数量。


## 四、数据集文件结构解读
### 1. 目录结构
**解压前**
```
dataset_compressed/
├── t10k-images-idx3-ubyte.gz                #测试集图像压缩包(1648877 bytes)
├── t10k-labels-idx1-ubyte.gz                #测试集标签压缩包(4542 bytes)
├── train-images-idx3-ubyte.gz                #训练集图像压缩包(9912422 bytes)
└── train-labels-idx1-ubyte.gz                #训练集标签压缩包(28881 bytes)
```
**解压后**
```
dataset_uncompressed/
├── t10k-images-idx3-ubyte                #测试集图像数据
├── t10k-labels-idx1-ubyte                #测试集标签数据
├── train-images-idx3-ubyte                #训练集图像数据
└── train-labels-idx1-ubyte                #训练集标签数据
```

### 2. 文件结构
该数据集将图像和标签都以矩阵的形式存储于一种称为idx格式的二进制文件中。该数据集的4个二进制文件的存储格式分别如下：

**训练集标签数据 (train-labels-idx1-ubyte):**

| 偏移量(bytes) | 值类型 | 数值	| 含义 |
|------ |------|-----|----|
|0	|32位整型	| 0x00000801(2049)|magic number|
|4	|32位整型	|60000|	有效数值的数量(即标签的数量)|
|8	|8位无符号整型|不定(0~9之间)|标签|
|...|	...|	...|	...|
|xxxx	|8位无符号整型|	不定(0~9之间)|标签|

**训练集图像数据(train-images-idx3-ubyte):**
| 偏移量(bytes)	| 值类型| 数值	| 含义|
|----|-----|----|---|
|0	|32位整型|	0x00000803(2051)|magic number|
|4	|32位整型|	60000|	有效数值的数量(即图像的数量)|
|8	|32位整型|	28	|图像的高(rows)|
12	|32位整型| 28|	图像的宽(columns)|
|16	|8位无符号整型|	不定(0~255之间)|图像内容|
|...|	...|	...|	...|
|xxxx|	8位无符号整型|	不定(0~255之间)|图像内容

**测试集标签数据(t10k-labels-idx1-ubyte):**
|偏移量(bytes)	|值类型	|数值 | 含义|
|--- |---- |----|----|
|0	|32位整型|	0x00000801(2049)|magic number|
|4	|32位整型|	10000|	有效数值的数量(即标签的数量)|
8	|8位无符号整型| 不定(0~9之间)|标签|
|...|	...|	...|	...|
|xxxx|	8位无符号整型|	不定(0~9之间)|标签|

**测试集图像数据 (t10k-images-idx3-ubyte):**
|偏移量(bytes)	|值类型	|数值	|含义|
|--- |---- | ---|---|
|0	|32位整型|	0x00000803(2051)|magic number|
|4	|32位整型|	10000|	有效数值的数量(即图像的数量)|
|8	|32位整型|	28	|图像的高 (rows)|
|12	|32位整型|	28	|图像的宽(columns)|
|16	|8位无符号整型|	不定(0~255之间)|图像内容|
|...|	...|	...|	...|
|xxxx|	8位无符号整型|	不定(0~255之间)|图像内容|


对于idx格式的二进制文件，其基本格式如下：
```
magic number
size in dimension 0
size in dimension 1
size in dimension 2 
.....
size in dimension N
data
```

每个idx文件都以magic number开头，magic number是一个4个字节，32位的整数，用于说明该idx文件的data字段存储的数据类型。

其中前两个字节总是0，第3个字节不同的取值代表了idx文件中data部分不同的数值类型，对应关系如下：

|取值	|含义|
|----|----|
|0x08|	8位无符号整型(unsigned char, 1 byte)|
|0x09	|8位有符号整型(char, 1 byte)|
|0x0B	|短整型(short, 2 bytes)|
|0x0C|	整型 (int, 4 bytes)|
|0x0D|	浮点型 (float, 4 bytes)|
|0x0E|	双精度浮点型 (double, 8 bytes)|

在MNIST数据集的4个二进制文件中，data部分的数值类型都是“8位无符号整型”，所以magic number的第3个字节总是0x08。

magic number的第4个字节代表其存储的向量或矩阵的维度。比如存储的是一维向量，那么magic number的第4个字节是0x01，如果存储的是二维矩阵，那么magic number的第4个字节就是0x02。

所以在MNIST数据集的4个二进制文件中，标签文件的magic number第4个字节都是0x01，而在图像文件中，因为一张图像的维度是2，而多张图像拼成的矩阵维度是3，所以图像文件magic number第4个字节都是0x03。

该数据集的官网说明了4个二进制文件中的整型数据是以大端方式 (MSB first) 存储的，所以在读取这4个二进制文件的前面几个32位整型数据时，需要注意声明数据存储格式是大端还是小端。

## 五、数据集下载链接
### 1. 数据集下载
OpenDataLab平台为大家提供了完整的数据集信息、直观的数据分布统计、流畅的下载速度、便捷的可视化脚本，欢迎体验。点击原文链接查看。

https://opendatalab.com/MNIST


参考资料

[1]Y LeCun,L Bottou,Y Bengio,etal.Gradient-based learning applied to document recognition[J].Proceedings of the IEEE,1998,86(11):2278-2324.

[2]http://yann.lecun.com/exdb/mnist/



还有哪些你关心的话题？

扫码入群,欢迎交流 
![二维码](https://mmbiz.qpic.cn/mmbiz_jpg/7yjDpC9UfD7NEyym4C8KBFplT20DM2vqAUAysVwzco8icviaYQ6McYIHep7ythBW0oZic97dXnhS6LbnoyibAqCbLQ/640?wx_fmt=jpeg&wxfrom=5&wx_lazy=1&wx_co=1)
添加小助手微信，发送“入群”，等待邀请
