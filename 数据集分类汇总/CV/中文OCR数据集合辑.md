# 收藏丨8个常用中文OCR数据集，附下载链接

随着深度学习技术的发展，智能OCR算法与应用也越来越丰富，对相关数据的需求也增加。

许多小伙伴反馈中文OCR数据集不好找，今天我们贴心地帮大家整理了8个常用的中文OCR数据集资源，记得收藏。

## No.1  MSRA-TD500 (MSRA Text Detection 500 Database)

下载链接：
https://opendatalab.com/MSRA-TD500


MSRA-TD500由华中科技大学于 2012 年在 CVPR 发布，是一个用于测试和评估多方向、多语言文字检测算法的自然图像数据集，包含500幅拍摄于室内（办公室和商场）和室外（街道）场景的自然图像。室内的图像主要包括标识、门牌和标牌等，室外的图像主要是路牌和广告牌等。图像的分辨率较高，介于1294*864和1920*1280之间。

该数据集由两部分构成：训练集、测试集。训练集中一共有300幅图像，通过随机抽样的形式从原始数据集中抽取出来。余下的200幅图像构成测试集。

数据集中的所有图像都经过完整标注。数据集的基本单元是文本行而非单词。

![图片1](https://mmbiz.qpic.cn/mmbiz_png/7yjDpC9UfD7YrgdNDSweibQyclCBzqzKC6QvK6ClrH6BqBjT6DhLlvMIaFJ4UeXDHj7gqibJGpcgZqhFgA5PxRUg/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)
MSRA-TD500数据集样例（图源：参考资料[1]）

MSRA-TD500数据集中的典型图像以及文字的标准矩形框 每一个矩形框对应一个文本行。红色的矩形框表示其中的文字被标记为“困难”。在MSRA-TD500数据集中，难以检测的文字（一般由低分辨率、模糊和遮挡等因素造成）会被标记为“困难”。


## No.2  Chinses Text in the Wild(CTW)

下载链接：
https://ctwdataset.github.io/


由清华大学与腾讯共同推出的一个大型中文自然文本数据集（Chinese Text in the Wild，CTW）。该数据集包含 32,285 张图像和 1,018,402 个中文字符。

每张图像尺寸为2048*2048，数据集大小为31GB。CTW以（8:1:1）的比例将数据集分为：

训练集（25887张图像，812872个中文字符）；
测试集（3269张图像，103519个中文字符）；
验证集（3129张图像，103519个中文字符）；

这些图像源于腾讯街景，从中国的几十个不同城市中捕捉得到。数据多样、复杂，它包含了平面文本、凸出文本、城市街景文本、乡镇街景文本、弱照明条件下的文本、远距离文本、部分显示文本等。

![图片2](https://mmbiz.qpic.cn/mmbiz_png/7yjDpC9UfD7YrgdNDSweibQyclCBzqzKCj7kVlHAq6cSAyrZc1Zv4w9vjXDWD8NXkIYCIzibIQRDYkeNjibv50BqQ/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)
CTW数据集样例示意（图源：参考资料[2]）

对于每张图像，数据集中都标注了所有中文字符。对每个中文字符，数据集都标注了其真实字符、边界框和 6 个属性以指出其是否被遮挡、有复杂的背景、被扭曲、3D 凸出、艺术化，和手写体等。


## No.3  Reading Chinses Text in the Wild(RCTW-17)

下载链接：
https://rctw.vlrlab.net/dataset.html

ICDAR（国际文档分析和识别大会）在2017年发起了一项专注于中文检测和识别比赛项目（RCTW），RCTW-17为竞赛数据集，它由12263张包含中文的自然场景图片组成，其中大部分是直接由摄像头或手机拍摄，少部分为生成图像，并且每张图像至少包含一行中文。图像尺寸不规则，数据集大小为11.4GB。

数据的标注均通过标注工具手工标注完成，通过绘制四边形来标注一个文本行，而不是以单词为单位进行标注，每个文本行的内容以UTF-8字符串进行标注。在数据集中存在字体、布局和语言等多样性。

数据集划分为两部分：训练集和验证集。训练集包含8034张图片，测试集包含4229张图片。

![图片3](https://mmbiz.qpic.cn/mmbiz_png/7yjDpC9UfD7YrgdNDSweibQyclCBzqzKCiaAaOP3g7WtJPlsfEZTwXhgibulzNN0ia51gDxMZcPoRibVVj8ccFd2PJA/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)
RCTW-17数据集样例示意（图源：参考资料[3]）


## No.4  ICPR MWI 2018挑战赛

下载链接：
https://tianchi.aliyun.com/competition/entrance/231685/information

ICPR MWI 大赛提供的包含2000张图像的官方数据集，主要由合成图像，产品描述，网络广告构成。该数据集数据量充分，中英文混合，涵盖数十种字体，字体大小不一，多种版式，背景复杂。数据集大小为2GB。其中训练集10000张，测试集10000张。

![图片4](https://mmbiz.qpic.cn/mmbiz_png/7yjDpC9UfD7YrgdNDSweibQyclCBzqzKCI2C0YibfKC8e3YIn8XV09wcRv3jdyhhDibPR2ApoUH6R0wf6e49d736w/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)
ICPR MWI 2018数据集标注样例，红框代表标注的文本框（图源：参考资料[4]）


## No.5  ShopSign

下载链接：
https://github.com/chongshengzhang/shopsign

该数据由河南大学科研团队发布的，是一个大规模中英文自然场景文本数据集，其包含25770张街景中文招牌图像，196010条文本行。

ShopSign中的图像是在不同的场景（市中心到偏远地区）中使用50多种不同的手机拍摄。相比于CTW，其包含了4000张夜间图像，同时也包含了2516对图像来对一个sign获取水平和多视角的图片。其包含多种分辨率，包括3024*4032、1920*1080、2180*720等。

CMT主要包含了几个主要发达城市，而ShopSign包含的地理范围广（北京、上海、厦门、新疆、蒙古、牡丹江、葫芦岛和河南省的一些城市和小城镇），包括许多街景车辆无法到达的郊区或小城镇。CMT使用了固定的拍摄角度，而ShopSign使用了多种角度进行拍摄。[5]

![图片5-1](https://mmbiz.qpic.cn/mmbiz_png/7yjDpC9UfD7YrgdNDSweibQyclCBzqzKCNQHLIy81H6Hfdt2LTEe5d9ic34RR2hxVMtudLI9kT19ticvjSaKURtdQ/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)
ShopSign数据集中广告牌样例示意（图源：参考资料[5]）

![图片5-2](https://mmbiz.qpic.cn/mmbiz_png/7yjDpC9UfD7YrgdNDSweibQyclCBzqzKCCN0tUGIzrSPdxVUtJY2C13dKrA2FicXREHicmG6WgCkz1gYwiagW64BMg/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)
ShopSign数据集中广告牌分类示意（图源：参考资料[5]）

注释包括了每个文本行的四边形边界框的坐标（顺序：左上、右上、右下、左下）以及相对应的文本行的相应文本。ShopSign仅仅处理广告牌上的文本。

## No.6  ICDAR2019-LSVT

下载链接：
https://github.com/chongshengzhang/shopsign

ICDAR 2019-LSVT（Large-scale Street View Text with Partial Labeling，弱标注大规模街景文字识别）国际学术竞赛公开的大规模弱标注场景文字数据集。

数据集采自中国街景，并由街景图片中的文字行区域（例如店铺标牌、地标等等）截取出来而形成。是首个提出弱标注数据的场景文字数据集，其中包括5万张精标注街景图像、40万张弱标注街景图像，总计45万张。

所有图像都经过一些预处理，将文字区域利用仿射变化，等比映射为一张高为48像素的图片。

![图片6-1](https://mmbiz.qpic.cn/mmbiz_png/7yjDpC9UfD7YrgdNDSweibQyclCBzqzKC2qd5qGooJibxiblfia0sjeGAKpzdJAX0uk1Tu2qQxe6aia1SURJkG6Gb1Q/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)
LSVT数据集精标注示意（图源：参考资料[6]）

![图片6-2](https://mmbiz.qpic.cn/mmbiz_png/7yjDpC9UfD7YrgdNDSweibQyclCBzqzKC3Iwf6NZnKOuvuoXANpFrUFlqzpJM5pGcjsNjBsP9GFUNviaNVcg07HQ/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)
LSVT数据集弱标注示意（图源：参考资料[6]）

## No.7  TotalText

下载链接：
https://opendatalab.com/TotalText

Total-Text是最大弯曲文本数据集之一-ArT（任意形状文本数据集）训练集中的一部分。该数据集共1555张图像，11459文本行，包含水平文本，倾斜文本，弯曲文本。文件大小441MB。大部分为英文文本，少量中文文本。其中训练集有1255张图像，测试集有300张图像。

![图片7](https://mmbiz.qpic.cn/mmbiz_png/7yjDpC9UfD7YrgdNDSweibQyclCBzqzKCK3yoG0vMkAruZdKYfc0Ih1VPCLeHVicJFwGibtUKqUcuotiayJhzoicgKw/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)
TotalText数据集样例示意（图源：OpenDataLab）

## No.8  Caffe-ocr中文合成数据

下载链接：
https://github.com/senlinuc/caffe_ocr

共360万张图片，图像分辨率为280*32，文件大小约为8.6GB。数据利用中文语料库（新闻+文言文），通过字体、大小、灰度、模糊、透视、拉伸等变化随机生成，字典中包含汉字、标点、英文、数字共5990个字符（语料字频统计，全角半角合并）。

每个样本固定10个字符，字符随机截取自语料库中的句子。按9:1分成训练集、验证集，测试集约6万张。

![图片8](https://mmbiz.qpic.cn/mmbiz_png/7yjDpC9UfD7YrgdNDSweibQyclCBzqzKCeDT8Oiaa2zoaBdeRqyv2yicpyqDEUjImpyU3ACtHk9Tic5BDhelLnyKlg/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)
Caffe-ocr数据集样例示意（图源：参考资料[7]）


##### 参考资料

[1]http://www.iapr-tc11.org/dataset/MSRA-TD500/Detecting_Texts_of_Arbitrary_Orientations_in_Natural_Images.pdf

[2]https://ctwdataset.github.io/

[3]https://arxiv.org/pdf/1708.09585v2.pdf

[4]https://tianchi.aliyun.com/competition/entrance/231685/information

[5]https://arxiv.org/pdf/1903.10412v1.pdf

[6]https://rrc.cvc.uab.es/?ch=16

[7]https://github.com/senlinuc/caffe_ocr



还有哪些你关心的话题？扫码入群,欢迎交流
![图片9](https://mmbiz.qpic.cn/mmbiz_jpg/7yjDpC9UfD7NEyym4C8KBFplT20DM2vqAUAysVwzco8icviaYQ6McYIHep7ythBW0oZic97dXnhS6LbnoyibAqCbLQ/640?wx_fmt=jpeg&wxfrom=5&wx_lazy=1&wx_co=1)
