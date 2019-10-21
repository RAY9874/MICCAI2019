# Multi Scale Curriculum CNN for Context-Aware Breast MRI Malignancy Classiﬁcation

## 任务目标：

乳腺癌分类

## 数据集：  

408张3D乳腺MRI (305恶性，103 良性)

## 创新点：

1.给定乳腺MRI 图，在不进行肿瘤定位的情况下（其他工作都需要定位出肿瘤，对肿瘤分类），使用一个3D CNN判断乳腺癌类别。

2.提出了一个 multi scale curriculum learning strategy ，先使用patch（大图中裁出来的小块）训练，再用大图训练。

## 模型及实验：

模型结构： resnet50 back bone

![1570781734669](./imgs/Multi Scale Curriculum CNN for Context-Aware Breast MRI Malignancy Classiﬁcation_model.jpg)

数据增强：旋转z轴±15°，5折交叉验证

对比Naive ResNet 、Mask RCNN 和 Retina Unet

## 结果



![1570781734669](./imgs/Multi Scale Curriculum CNN for Context-Aware Breast MRI Malignancy Classiﬁcation_results.jpg)

## 心得

⭐（一共5个星）

1.数据集较少

408张图很容易过拟合，即使增强一些，泛化能力也有限

2.对比实验不合理

maskrcnn是二阶段目标检测模型。与论文提出的分类任务有些不同。



# Models Genesis: Generic Autodidactic Models for 3D Medical Image Analysis

## 任务目标

在7个公开的医疗目标检测数据集上得第一

论文原话：

> Can we utilize the large number of available Chest CT images without systematic annotation to train source models that can yield high-performance target models via transfer learning?

## 数据集

7个公开数据集

## 创新点

## 模型实验

## 结果

## 心得

















# Quantifying and Leveraging Classiﬁcation Uncertainty for Chest Radiograph Assessment

## 任务目标

胸片疾病分类

## 数据集

ChestXRay8  和  PLCO 

## 创新点

在分类的同时加入一个 ”uncertainty measure“，如果不确定性小于阈值，就人工判断。

>  i.e., set a threshold ut and steer the system to not output its prediction on all cases with an expected uncertainty larger than ut. 
>
> Instead, these cases are labeled with the message.  ”Do not know for sure; process case manually”.

以下说明了使用他们这种方式性能可以提升特别大（当然了。。设置成100%准确率能到1。。。）

>  For example, for the identiﬁcation of granuloma, a rejection rate of 25% leads to an increase of over 20% in the micro-average F1 score. On the same abnormality, a 50% rejection rate leads to a F1 score over 0.99 for the prediction of negative cases

## 模型实验

模型：densenet121

## 结果

他们的准确率比较高

![1570781734669](.\imgs\Quantifying and Leveraging Classiﬁcation Uncertainty for Chest Radiograph Assessment model .JPG)

## 心得

⭐

实在是太水了。。。



# Accurate Esophageal Gross Tumor Volume Segmentation in PET/CT using Two-Stream Chained 3D Deep Network Fusion

## 任务目标

肿瘤体积分割

## 数据集

对110名食管癌患者进行了广泛的5倍交叉验证，这是迄今为止**最大**的一次分析

## 创新点

利用rtct和正电子发射断层成像（pet）两种成像方式（多模态），使gtv分割更加精确   (其他工作不使用pet图像)

![1570781734669](.\imgs\Accurate Esophageal Gross Tumor Volume Segmentation in PETCT using Two-Stream Chained 3D Deep Network Fusion sample.JPG)

## 模型实验

双路的Unet变种（decoder端加了与FPN相似的结构）

![1570781734669](.\imgs\Accurate Esophageal Gross Tumor Volume Segmentation in PETCT using Two-Stream Chained 3D Deep Network Fusion model.JPG)

## 结果

使用了三种评价指标，好像是比较偏门的评价指标，结果当然是论文提出的方法（PSNN）比较好

DSC

Hausdorﬀ distance (HD) in “mm”

and average surface distance with respect to the ground truth contour (ASDGT) in “mm”

![1570781734669](.\imgs\Accurate Esophageal Gross Tumor Volume Segmentation in PETCT using Two-Stream Chained 3D Deep Network Fusion result.JPG)

## 心得

⭐⭐

Unet 结构比较普遍，PHNN是作者在2017年MICCAI上提出的模型，本篇文章将二者优势结合取得了更好的结果，可见Unet+FPN结构在实例分割任务上确实强大









# Dual-Stream Pyramid Registration Network



## 任务目标

无监督3D图像配准

> 什么是图像配准：**图像配准是使用某种方法，基于某种评估标准，将一副或多副图片（局部）最优映射到目标图片上的方法**，例如图像会来自不同的采集设备，取自不同的时间，不同的拍摄视角等等，有时也需要用到针对不同对象的图像配准问题。具体地说，对于一组图像数据集中的两幅图像，通过寻找一种空间变换把一幅图像映射到另一幅图像，使得两图中对应于空间同一位置的点一一对应起来，从而达到信息融合的目的（配准的好的话，理论上可以提升图像清晰度）

附论文原文对于任务目标的解释：

> The goal of 3D medical image registration is to estimate a deformation ﬁeld Φ which can warp a moving volume M ⊂ R3 to a ﬁxed volume F ⊂ R3, so that the warped volume W = M ◦Φ ⊂ R3 can be accurately aligned to the ﬁxed one F. 

## 数据集

LPBA40 

> contains 40 T1-weighted MR images, each of which was annotated with 56 subcortical ROIs. 

Mindboggle101 

> contains 101 T1weighted MR images, which were annotated with 25 cortical regions, and can be used to evaluate registration results regarding ﬁne brain structure.

## 创新点

## 模型实验

输入：move image + fixed image

输出：配准后的图片

![1570781734669](.\imgs\Dual-Stream Pyramid Registration Network model.JPG)

## 结果

使用他们的方法在医疗数据集上取得了约10个点的提升

> we evaluate our model on the LPBA40 and the Mindboggle101, where our method improved the results of VoxelMorph [2] considerably, with 0.683→0.778 and 0.511→ 0.631 respectively, in term of average Dice score.

 对比实验VoxelMorph 是2017年CVPR一篇论文提出的模型

![1570781734669](.\imgs\Dual-Stream Pyramid Registration Network result.JPG)

## 心得

⭐⭐

无监督方法，理论上来说，给他们数据立刻就可以训练。医生比较喜欢

使用他们的方法在医疗数据集上取得了约10个点的提升,可见对于医疗问题具有较高针对性

数据集并不大，可能存在过拟合的情况。存疑

不太知道这玩意落地的话，到底有啥用？





# PseudoEdgeNet: Nuclei Segmentation only with Point Annotations



## 任务目标

弱监督 Nuclei segmentation  （实例分割任务，标注时仅仅用一个点代替mask表示细胞的位置）

## 数据集

MoNuSeg （30张）and TNBC（50张） （公开）

## 创新点

## 模型实验

![1570781734669](.\imgs\PseudoEdgeNet Nuclei Segmentation only with Point Annotations model.JPG)

PseudoEdgeNet（g（I）） ：with four convolution layers

attention module h(I) : FPN with a Resnet-18 backbone and stack a sigmoid as an output layer. 

## 结果

![1570781734669](.\imgs\PseudoEdgeNet Nuclei Segmentation only with Point Annotations result.JPG)

## 心得

⭐⭐⭐

非常巧妙的利用了CNN低维特征提取边界、纹理的特性。仅仅使用一个点的标注就能提取到超越mask标注的效果。

但是看模型结构输入图中，本身其边界特征就比较明显。估计只使用sobel算子也能提个差不多。



# Model-based Convolutional De-Aliasing Network Learning for Parallel MR Imaging

## 任务目标

使用神经网络对fmri图像进行去除噪声

## 数据集

未公开

模型：<img src=".\imgs\{70094EA7-13E1-4251-BA30-66371249BAA3}.png.jpg" style="zoom: 50%;" />

方法：<img src=".\imgs\{84D165C8-F854-4971-94F8-B59CDE19221A}.png.jpg" style="zoom:50%;" />

指标：<img src=".\imgs\{0A3FF8D8-8F64-4502-8D76-471C95FC267E}.png.jpg" style="zoom:50%;" />

# Detection and Correction of Cardiac MR Motion Artefacts during Reconstruction from k-space

# 任务目标

图像重建时的检测和纠正

# 数据集

未公开

流程图：<img src=".\imgs\{7AA47354-5E77-4276-8383-C9CA1241DD37}.png.jpg" style="zoom:50%;" />

模型：<img src=".\imgs\{1C779A41-701B-4C86-8122-6FD9A403D3A8}.png.jpg" style="zoom:50%;" />

指标：<img src=".\imgs\{9DA9CF99-9098-4D0D-80D8-E673552CFE1A}.png.jpg" style="zoom:50%;" />



# Artifact Disentanglement Network for Unsupervised Metal Artifact Reduction

## 任务目标

通过无监督方式减少伪影

## 数据集

未公开

模型：<img src=".\imgs\{DB2B4476-ECED-440F-9450-CB2B43AF31A6}.png.jpg" style="zoom:50%;" />

指标：<img src=".\imgs\{B139CBFB-923F-4A7D-9B99-DA4E837D9437}.png.jpg" style="zoom:50%;" />

# Learning shape priors for robust cardiac MRI segmentation from multi-view images

## 工作内容

多视图mri图像分割

## 数据集

未公开

模型：二阶段模型。首先shape mae学习先验知识，然后mv-unet进行分割。

<img src=".\imgs\{3E1CE14A-67A9-4AD8-A5A1-358A4EC604D3}.png.jpg" style="zoom:50%;" />

<img src=".\imgs\{B175C98A-D589-4887-82C5-42668BC38AD5}.png.jpg" style="zoom:50%;" />

指标：<img src=".\imgs\{7D75AF6A-21DF-4FED-B37C-FCE1D21E0363}.png.jpg" style="zoom:50%;" />

# VS-Net: Variable splitting network for accelerated parallel MRI reconstruction

## 任务目标

对mri图像内容进行重建

模型：<img src=".\imgs\{F17C665B-A56B-42C2-80C5-6751A05853F5}.png.jpg" style="zoom:50%;" />

<img src=".\imgs\{AD81608C-CD5C-4706-96A0-4416F0BE485F}.png.jpg" style="zoom:50%;" />





