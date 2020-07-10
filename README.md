# 基于内容图像检索系统

### 一、相关代码文件说明

1. 直接在MATLAB中打开`Content_based_Image_Retrieval.mlapp`，每个按键的功能都在用户界面显示了，相关回调函数也根据功能实现，可以自行根据想要的功能查看。
2. `cal_mAP_codes.rar`压缩包中的代码文件用于计算系统的mAP，`getResultFile***128D`和`getResultFile***4096D`分别为根据官方给出的groundtruth文件在128维数或4096维数下的检索输出排名文件，用于之后计算mAP使用；`calMAP***128D.m`和`calMAP***4096D.m`则分别使用前面获得的排名为文件计算某数据集在128维数或4096维数下的mAP。

### 二、相关数据文件说明

1. `imagenet-vgg-f.mat`文件是MatConvNet提供的VGG网络预训练模型，可直接使用。
2. Data文件夹中存放的是程序所需的所有数据文件。其中`resultFile***---D.dat`为某数据集在相应维数下根据groundtruth文件检索输出的排名文件；`***FeaturesNorm.mat`用于存储某数据集所有图像在4096维数下的特征向量；`***128D.mat`则存储某数据集所有图像在128维数下的特征向量；`gnd_Oxford.mat`为官方给出的Oxford5k数据集groundtruth信息综合文件；`holidays_images.dat`也是官方给出的文件，用于计算Holidays数据集的mAP。

### 三、APP使用教程

1. 首先要选择训练模型。点击Select A Model即可选择文件，直接使用`imagenet-vgg-f.mat`文件即可。

<p align="center">选择训练模型</p>
<p align="center"><img src="https://github.com/GaryVillzoy/Content-based-Image-Retrieval/blob/master/README_images/1.png"  width = 400 alt="search result"/></p>

2. 然后要回答一些问题，比如MatConvNet是否已经编译过和选择的数据集是否为mat文件（即数据集是否已经完成特征提取）。如果网络为编译过，则之后系统会自动进行编译，不过需要一点时间。如果数据集没有完成特征提取，则之后选择数据集文件夹，系统会自动进行特征提取，但也要消耗一点时间。

   <p align="center">勾选回答问题</p>
   <p align="center"><img src="https://github.com/GaryVillzoy/Content-based-Image-Retrieval/blob/master/README_images/2.png"  width = 400 alt="search result"/></p>

3. 之后就是根据前面回答的问题进行数据集的选取并判断是否需要提取特征向量。如果前面勾选了数据集是mat文件的话这里的数据集只能选择mat文件，且系统自动根据文件名字判断数据的维数；反之则只能选择文件，Extract features按钮将可用，用户需手动选择提取的特征维数。

   <p align="center">数据集相关操作</p>
   <p align="center"><img src="https://github.com/GaryVillzoy/Content-based-Image-Retrieval/blob/master/README_images/3.png"  width = 400 alt="search result"/></p>

4. 最后就是开始检索。用户可通过调整Retrieval Number来选择检索结果返回图片数，然后点击Start retrieval选择需要检索的图像，然后等待输出结果即可。

<p align="center">开始检索</p>
<p align="center"><img src="https://github.com/GaryVillzoy/Content-based-Image-Retrieval/blob/master/README_images/4.png"  height = 250 width = 300 alt="search result"/></p>

5. 检索结果可直接在用户界面下方看到。排名从高到低会从左到右输出，并且输出此次检索的用时。如果用户选择的返回结果图片数大于3，则结果会通过弹窗的方式显示。

<p align="center">返回结果</p>
<p align="center"><img src="https://github.com/GaryVillzoy/Content-based-Image-Retrieval/blob/master/README_images/5.png"  height = 200 width = 500 alt="search result"/></p>

6. 在用户界面最下方可以选择数据集，并点击Calculate按钮计算数据集在该系统下的mAP。

<p align="center">计算mAP</p>
<p align="center"><img src="https://github.com/GaryVillzoy/Content-based-Image-Retrieval/blob/master/README_images/6.png"  height = 35 width = 400 alt="search result"/></p>

### 四、注意事项

1. 请务必提前了解MatConvNet工具箱。

2. 请自行在官网下载预训练模型，本系统初步使用的预训练模型为imagenet-vgg-f.mat。
