# 详细解读：MIT经典的语义分割数据集ADE20K，附下载链接

小伙伴们，乐于分享的OpenDataLab来啦！这次，给大家带来一份ADE20K 数据集的详细使用“攻略”，助大家模型训练一臂之力。

这个由MIT 发布的大型数据集，可用于场景感知、解析、分割、多物体识别和语义理解，不容错过图片

## 一、数据集简介
**发布方：** MIT CSAIL Computer Vision Group

**发布时间：** 2016

**背景：** 
视觉场景的语义理解是计算机视觉的关键问题。尽管社区在数据收集方面做出了努力，但仍然很少有图像数据集涵盖广泛的场景和对象类别，而且缺乏具有用于场景理解的逐像素注释。

**简介：**
ADE20K涵盖了场景、对象、对象部分的各种注释，在某些情况下甚至是部分的部分。有25k张复杂日常场景的图像，其中包含自然空间环境中的各种对象。每个图像平均有19.5个实例和10.5个对象类。

## 二、数据集详细信息

### 1. 标注数据量

● 训练集：20210张图像

● 验证集：2000张图像

● 测试集：3000张图像

### 2. 标注类别

数据集的标注包含三种视觉概念：

● 离散对象（discrete object），它是具有明确定义的形状的事物，例如汽车、人；

● 包含无定形背景区域的东西（stuff），例如草、天空；

● 对象部分（object part），它是某些具有功能意义的现有对象实例的组件，例如头部或腿部。

三种视觉概念共标注类别3169类，其中离散对象和无定形背景区域的东西有2693类。对象部分有476类。

### 3. 可视化
![图片1](https://mmbiz.qpic.cn/mmbiz_png/7yjDpC9UfD7XWFH45QC63ia6q7NlsM3qW816IkiaQ4dcsuPo51UVbCjGYFu9VY1skDuzw81TAdHVvT6BJxCajs1Q/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

图1：第一行显示样本图像，第二行显示对象的标注，第三行显示对象部分的标注。颜色方案同时编码对象类别和对象实例，即不同的对象类别具有较大的色差，而来自同一对象类别的不同实例具有较小的色差（例如，第一张图像中的不同人实例具有略微不同的颜色）。


## 三、数据集任务定义及介绍
### 1. 场景解析
**● 定义**
场景解析是将整个图像密集地分割成语义类，其中每个像素都被分配一个类标签，例如树的区域和建筑物的区域。

**● 基准**
作者选择 ADE20K 数据集中按其总像素比排名的前150个类别，并构建 ADE20K 的场景解析基准，称为 SceneParse150。

在150个类别中，有35个东西类（即墙壁、天空、道路）和115个离散对象类（即汽车、人、桌子）。150个类的标注像素占数据集所有像素的92.75%，其中无定形背景区域的东西类占60.92%，离散对象类占31.83%。

结果以通常用于语义分割的四个指标报告：

- Pixel accuracy（像素精度）：表示正确分类的像素的比例；
- Mean accuracy（平均准确度）：表示在所有类别中平均正确分类的像素的比例；
- Mean IoU（平均 IoU）：表示预测像素和真实像素之间的交并比，在所有类上平均；
- Weighted IoU（加权IoU）：表示按每个类的总像素比加权的 IoU。


### 2. 实例分割
**● 定义**
实例分割是检测图像中的对象实例，并进一步生成对象的精确分割掩码。它与场景解析任务的不同之处在于，场景解析中没有分割区域的实例概念，而在实例分割中，如果场景中有三个人，则需要网络对每个人区域进行分割。

**● 基准**
为了对实例分割的性能进行基准测试，作者从完整数据集中选择了100个前景对象类别，将其称为 InstSeg100。InstSeg100 中对象实例总数为 218K，平均每个对象类别有2.2K个实例，每个图像有10个实例；除船舶外的所有对象都有超过100个实例。

结果以如下指标报告：
一个总体度量平均精度 mAP，以及不同对象尺度上的度量，用mAP_S（小于32×32像素的对象）、mAP_M（在32×32和96×96像素之间）和 mAP_L（大于96×96像素）。

## 四、数据集文件结构解读
目录结构：（语言：Python）
```ADE20K_2021_17_01/
    images/
        training/
            cultural/
                apse__indoor/
                    <filename0>.jpg         # 原图像
                    <filename0>_seg.png     # 分割图，通道R和G编码对象类别ID，
                                            # 通道B编码实例ID
                    <filename0>_parts_{i}.png 
                                            # 部件分割图,i表示第i层部件，如car
                                            # 属于第一层部件，wheel属于第二层部件
                    <filename0>.json        # 存储图像中所有实例的多边形，属性等信息
                    <filename0>/            # 存储图像中所有实例mask的目录
                        instance_000_<filename0>.png
                        instance_001_<filename0>.png
                    ...
                ...
            ...
        validation/
            cultural/
                apse__indoor/
                    <filename1>.jpg
                    <filename1>_seg.png
                    <filename1>_aprts_{i}.png
                    <filename1>.json
                    <filename1>/
                        instance_000_<filename1>.png
                        instance_001_<filename1>.png
                        ...
                    ...
                ...
            ...
    index_ade20k.pkl                    # 数据和存储图像的文件夹的统计信息
```

<filename>.json文件格式：
```
{
    "annotation": {
        "filename": "<filename>.jpg",   # 图像名称
        "folder": "ADE20K_2021_17_01/images/ADE/training/urban/street",
                                        # 图像存储的相对路径
        "imsize": [                     # 图像高、宽、通道数
            1536,
            2048,
            3
        ],
        "source": {                     # 图像来源信息
            "folder": "static_sun_database/s/street",
            "filename": "labelme_acyknxirsfolpon.jpg",
            "origin": ""
        },
        "scene": [                      # 图像场景信息
            "outdoor",
            "urban",
            "street"
        ],
        "object": [                     # 标注实例列表
            {
                "id":0,                 # 实例ID
                "name":"traffic light, traffic signal, stoplight",
                                        # 实例标签
                "name_ndx": 2836,       # 实例标签
                "hypernym": [           # 上位词
                    "traffic light, traffic signal, stoplight",
                    "light",
                    "visual signal",
                    "signal, signaling, sign",
                    "communication",
                    "abstraction, abstract entity",
                    "entity"
                ],
                "raw_name": "traffic light",
                "attributes": [],       # 属性
                "depth_ordering_rank": 1,
                                        # 深度顺序
                "occluded": "no",       # 遮挡情况
                "crop": "0",
                "parts": {              # 部件信息
                    "hasparts": [],
                    "ispartof": [],
                    "part_level": 0
                },
                "instance_mask": "<filename>/instance_000_<filename>.png",
                                        # 对应的实例mask
                "polygon": {            # 多边形坐标
                    "x": [346, ...],
                    "y": [781, ...]
                },
                "saved_date": "18-Dec-2005 06:56:48"
            },
            ...
        ]
```

![图片2](https://mmbiz.qpic.cn/mmbiz_png/7yjDpC9UfD7XWFH45QC63ia6q7NlsM3qWKgP6w4vtRZa1w8sGxiazjrN6fnp2stc9xyClVHMbsargDkF9fHegUDw/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)
图2: index_ade20k.pkl 文件用Python打开后的格式


**index_ade20k.pkl 里各个字段含义：**
- **filename**：长度为 N=27574 的数组，带有图像文件名。
- **folder**：包含图像文件夹名称的长度为 N 的数组。
- **objectIsPart**：是对象部分的对象类别. 大小为 [C, N] 的数组，计算一个对象在每个图像中成为一部分的次数。objectIsPart[c,i]=m 如果在图像 i 中对象类 c 是另一个对象的一部分 m 次。
- **objectPresence**：大小为 [C, N] 的数组，每个图像的对象计数。objectPresence(c,i)=n 如果在图像 i 中有 n 个对象类 c 的实例。
- **objectcounts**：长度为 C 的数组，每个对象类的实例数。
- **objectnames**：带有对象类名的长度为 C 的数组。
- **proportionClassIsPart**：长度为 C 的数组，其中 c 类作为一部分的次数比例。如果 ratioClassIsPart[c]=0 则意味着这是一个主要对象（例如，汽车、椅子……）。
- **scene**：长度为 N 的数组，为每个图像提供场景名称（与 Places 数据库相同的类）
- **wordnet_found**：长度为 C 的数组。它表示是否在 Wordnet 中找到了对象名。
- **wordnet_level1**：长度为C 的列表。WordNet 关联的列表。
- **wordnet_synset**：长度为 C 的列表。每个对象名称的 WordNet 同义词集。
- **wordnet_hypernym**：长度为 C 的列表。每个对象名称的 WordNet 上位词列表。
- **wordnet_gloss**：长度为 C 的列表。存的是WordNet同义词集合对应的定义。
- **wordnet_frequency**：长度为 C 的数组。每个WordNet同义词集合出现的次数。
- **description**：对index ade20k.pkl中每个字段的描述。

## 五、数据集资源
OpenDataLab平台已经上架了ADE20K数据集，为大家提供了完整的数据集信息、流畅的下载速度，快来体验吧！

ADE20K 2021数据集
https://opendatalab.com/120



#### 参考资料：

[1]官网：https://groups.csail.mit.edu/vision/datasets/ADE20K/

[2]论文：Semantic Understanding of Scenes through ADE20K Dataset. Bolei Zhou, Hang Zhao, Xavier Puig, Tete Xiao, Sanja Fidler, Adela Barriuso and Antonio Torralba. International Journal on Computer Vision (IJCV).[PDF]

[3]Github：https://github.com/CSAILVision/ADE20K


还有哪些你关心的话题？

扫码入群,欢迎交流
![图4](https://mmbiz.qpic.cn/mmbiz_jpg/7yjDpC9UfD7NEyym4C8KBFplT20DM2vqAUAysVwzco8icviaYQ6McYIHep7ythBW0oZic97dXnhS6LbnoyibAqCbLQ/640?wx_fmt=jpeg&wxfrom=5&wx_lazy=1&wx_co=1)
添加小助手微信，发送“入群”，等待邀请