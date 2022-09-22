# CityScapes数据集

## 1. 数据集简介
**发布方**：  
Daimler AG R&D, TU Darmstadt, MPI Informatics  

**发布时间**：2015

**背景**：聚焦于城市街道场景的语义理解。

**简介**：CityScapes数据集有以下特点：
- 标注多样，包含实例分割、语义分割、多边形框等三种标注
- 类别复杂，30+类别，同时包含group和class两个维度描述
- 场景差异，涵盖50个城市、不同季节、不同时段（白天）
- 体量庞大，拥有5000精标注图片和20000粗标注图片

## 2. 数据集详细信息
### 2.1 标注数据量（以精标注为例）
- 训练集：2975张图像
- 验证集：500张图像
- 测试集：1525张图像

这里每一张图片都同时拥有三个标注文件（实例分割、语义分割、多边形框标注）

### 2.2 标注类别
标注的30+类别及其所在的组如下所示：
|Group|Class|
|-- |-- |
|flat|road · sidewalk · parking+ · rail track+|
|human|person* · rider*|
|vehicle|car* · truck* · bus* · on rails* · motorcycle* · bicycle* · caravan*+ · trailer*+|
|construction|building · wall · fence · guard rail+ · bridge+ · tunnel+|
|object|pole · pole group+ · traffic sign · traffic light|
|nature|vegetation · terrain|
|sky|sky|
|void|ground+ · dynamic+ · static+|

其中，*表示部分区域连在一起的实例，会作为一个整体来标注，比如"car group"；+表示该类别不包含在验证集中，并被视为无效的。

### 2.3. 可视化
精标注的可视化效果如下所示：
![图片1](https://mmbiz.qpic.cn/mmbiz_png/7yjDpC9UfD6jy7tz44BpDib66D60FoO7JMGtLaSmAlB3IVSMRXbjagqpTe2aDPgiaPW6N63UaGDH1Dj7da25teKw/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

## 3. 数据集任务定义及介绍
### 3.1 语义分割
**场景解析定义**
场景解析是将整个图像密集地分割成语义类，其中每个像素都被分配一个类标签，例如树的区域和建筑物的区域。

-**场景解析评价指标**
通常用于语义分割的四个指标指标：
- Pixel Accuracy（像素准确度，PA）表示正确分类的像素的比例；
- Mean Pixel Accuracy（平均像素准确度，MPA）表示所有类别中正确分类的像素比例的平均。
- Mean Intersection over Union（平均交并比，MIoU）表示预测像素和真实像素之间的交并比，在所有类上平均。
- Weighted IoU（加权交并比，WIoU）表示按每个类的总像素比加权的交并比。

### 3.2 实例分割
**实例分割定义**
实例分割是检测图像中的对象实例，并进一步生成对象的精确分割掩码。 它与场景解析任务的不同之处在于，场景解析中没有分割区域的实例概念，而在实例分割中，如果场景中有三个人，则需要网络对每个人区域进行分割。

**实例分割评价指标**
实例分割一般有以下几个评价指标：
- Average Precision（平均精度，AP）准确率的平均值，其中准确率P = TP/（TP+FP）；
- Pixel Accuracy（像素准确度，PA）表示正确分类的像素的比例；
- Mean Pixel Accuracy（平均像素准确度，MPA）表示所有类别中正确分类的像素比例的平均。
- Mean Intersection over Union（平均交并比，MIoU）表示预测像素和真实像素之间的交并比，在所有类上平均。
- Weighted IoU（加权交并比，WIoU）表示按每个类的总像素比加权的交并比。

## 4. 数据集文件结构解读
### 4.1 目录结构
目录结构（这里以精标注的为例）：
```
dataset_root/
├── gtFine/
|  ├── test/                                                  # 测试集
|  |  ├── berlin/                                             # 城市名称
|  |  |  ├── berlin_000543_000019_gtFine_color.png            # 可视化的分割图
|  |  |  ├── berlin_000543_000019_gtFine_instanceIds.png      # 实例标注文件
|  |  |  ├── berlin_000543_000019_gtFine_labelIds.png         # 语义分割标注文件
|  |  |  ├── berlin_000543_000019_gtFine_polygons.json        # 存储各个类的名称和相应的区域边界
|  |  |  └── ...
|  |  ├── bielefeld/                                          # 城市名称
|  |  |  ├── bielefeld_000000_066495_gtFine_color.png         # 可视化的分割图
|  |  |  ├── bielefeld_000000_066495_gtFine_instanceIds.png   # 实例标注文件
|  |  |  ├── bielefeld_000000_066495_gtFine_labelIds.png      # 语义分割标注文件
|  |  |  ├── bielefeld_000000_066495_gtFine_polygons.json     # 存储各个类的名称和相应的区域边界
|  |  |  └── ...
|  |  └── ...
|  ├── train/                                                 # 训练集
|  |  ├── aachen/                                             # 城市名称
|  |  |  ├── aachen_000000_000019_gtFine_color.png            # 可视化的分割图
|  |  |  ├── aachen_000000_000019_gtFine_instanceIds.png      # 实例标注文件
|  |  |  ├── aachen_000000_000019_gtFine_labelIds.png         # 语义分割标注文件
|  |  |  ├── aachen_000000_000019_gtFine_polygons.json        # 存储各个类的名称和相应的区域边界
|  |  |  └── ...
|  |  └── ...
|  └── val/
|     ├── frankfurt/                                          # 城市名称
|     |  ├── frankfurt_000000_000294_gtFine_color.png         # 可视化的分割图
|     |  ├── frankfurt_000000_000294_gtFine_instanceIds.png   # 实例标注文件
|     |  ├── frankfurt_000000_000294_gtFine_labelIds.png      # 语义分割标注文件
|     |  ├── frankfurt_000000_000294_gtFine_polygons.json     # 存储各个类的名称和相应的区域边界
|     |  └── ...
|     └── ...
└── leftImg8bit/
   ├── test/
   |  ├── berlin/                                             # 城市名称
   |  |  ├── berlin_000543_000019_leftImg8bit.png             # 测试集图片
   |  |  └── ...
   |  ├── bielefeld/                                          # 城市名称
   |  |  ├── bielefeld_000000_066495_leftImg8bit.png          # 测试集图片
   |  |  └── ...
   |  └── ...
   ├── train/
   |  ├── aachen/                                             # 城市名称
   |  |  ├── aachen_000000_000019_leftImg8bit.png             # 测试集图片
   |  |  └── ...
   |  └── ...
   └── val/
      ├── frankfurt/                                          # 城市名称
      |  ├── frankfurt_000000_000294_leftImg8bit.png          # 测试集图片
      |  └── ...
      └── ...
```
### 4.2 标注格式
Cityscapes数据共有两种标注格式，分别是实例分割及语义分割所采用的分割图格式（.png文件），以及多边形边框的json格式（.json文件）。其中，png文件为灰度图片，尺寸和原始图片尺寸相同，其像素上的灰度值对应原始图片对应像素的类别id（或实例id），实例分割图中实例id对应的类别id则需要同时结合语义分割图中相同像素坐标的类别id来获取。分割图的可视化效果图可参考前文1.3的可视化部分。

json标注的文件格式如下所示：
```
{
    "imgHeight": 1024,
    "imgWidth": 2048,
    "objects": [
        {
            "label": "ego vehicle",
            "polygon": [
                [
                    271,
                    1023
                ],
                [
                    387,
                    1009
                ],
                ...
            ]
        },
        ...
    ]
}
```
其中包含的字段如下：
|属性名称|含义|数据类型|
|---|---|---|
|imgHeight|图像高度|int|
|imgWidth|图像宽度|int|
|objects|实例列表|list|
|label|类别名称|str|
|polygon|边界点坐标|list|


## 5. 数据集标准化
OpenDataLab平台为大家提供了CityScapes数据集完整的数据集信息、直观的数据分布统计、流畅的下载速度、便捷的可视化脚本，欢迎体验。

CityScapes
https://opendatalab.com/CityScapes


*参考资料*

[1]官网：https://www.cityscapes-dataset.com/

[2]论文：M. Cordts, M. Omran, S. Ramos, T. Rehfeld, M. Enzweiler, R. Benenson, U. Franke, S. Roth, and B. Schiele, The Cityscapes Dataset for Semantic Urban Scene Understanding, in CVPR, 2016.

(论文下载链接：https://www.cityscapes-dataset.com/wordpress/wp-content/papercite-data/pdf/cordts2016cityscapes.pdf）

[3]Github：https://github.com/mcordts/cityscapesScripts