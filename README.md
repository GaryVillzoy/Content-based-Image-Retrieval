# 基于内容图像检索系统

### 一、关于可执行程序须知

1. 对于**安装有MATLAB的用户**可直接运行使用`CBIR_Demo.exe`文件，或是直接运行`Content_based_Image_Retrieval.mlapp`文件；否则应运行`CBIR_Demo_web.exe`文件进行Runtime的安装，再进行使用。

   【**注意**】`CBIR_Demo.exe`文件只是该系统的简单样例示范模型，因系统使用了$$MEX$$，在打包时会出问题，所以想要测试完整功能请使用$$MATLAB$$运行`CBIR_Demo_web.exe`。

### 二、相关代码文件说明

1. 我在系统代码编写过程中没有编写`.m`文件，所有代码直接在$$MATLAB$$的$$APP$$设计工具中编写，故要查看源代码可直接在$$MATLAB$$中打开`Content_based_Image_Retrieval.mlapp`查看，每个按键的功能都在用户界面显示了，相关回调函数也根据功能实现，可以自行根据想要的功能查看。
2. `cal_mAP_codes.rar`压缩包中的代码文件用于计算系统的$$mAP$$，`getResultFile***128D`和`getResultFile***4096D`分别为根据官方给出的$$groundtruth$$文件在128维数或4096维数下的检索输出排名文件，用于之后计算$$mAP$$使用；`calMAP***128D.m`和`calMAP***4096D.m`则分别使用前面获得的排名为文件计算某数据集在128维数或4096维数下的$$mAP$$。

### 三、相关数据文件说明

1. `imagenet-vgg-f.mat`文件是MatConvNet提供的VGG网络预训练模型，可直接使用。
2. $$Data$$文件夹中存放的是程序所需的所有数据文件。其中`resultFile***---D.dat`为某数据集在相应维数下根据$$groundtruth$$文件检索输出的排名文件；`***FeaturesNorm.mat`用于存储某数据集所有图像在4096维数下的特征向量；`***128D.mat`则存储某数据集所有图像在128维数下的特征向量；`gnd_Oxford.mat`为官方给出的$Oxford5k$数据集$$groundtruth$$信息综合文件；`holidays_images.dat`也是官方给出的文件，用于计算$Holidays$数据集的$$mAP$$。

### 四、APP使用教程

1. 首先要选择训练模型。点击$$Select A Model$$即可选择文件，直接使用`imagenet-vgg-f.mat`文件即可。

<p align="center">选择训练模型</p>
<p align="center"><img src="https://github.com/GaryVillzoy/Content-based-Image-Retrieval/blob/master/README_images/1.png"  width = 400 alt="search result"/></p>

2. 然后要回答一些问题，比如$$MatConvNet$$是否已经编译过和选择的数据集是否为$$mat$$文件（即数据集是否已经完成特征提取）。如果网络为编译过，则之后系统会自动进行编译，不过需要一点时间。如果数据集没有完成特征提取，则之后选择数据集文件夹，系统会自动进行特征提取，但也要消耗一点时间。

   <p align="center">勾选回答问题</p>
   <p align="center"><img src="https://github.com/GaryVillzoy/Content-based-Image-Retrieval/blob/master/README_images/2.png"  width = 400 alt="search result"/></p>

3. 之后就是根据前面回答的问题进行数据集的选取并判断是否需要提取特征向量。如果前面勾选了数据集是$$mat$$文件的话这里的数据集只能选择$$mat$$文件，且系统自动根据文件名字判断数据的维数；反之则只能选择文件，$$Extract\ features$$按钮将可用，用户需手动选择提取的特征维数。

   <p align="center">数据集相关操作</p>
   <p align="center"><img src="https://github.com/GaryVillzoy/Content-based-Image-Retrieval/blob/master/README_images/3.png"  width = 400 alt="search result"/></p>

4. 最后就是开始检索。用户可通过调整$$Retrieval\ Number$$来选择检索结果返回图片数，然后点击$$Start\ retrieval$$选择需要检索的图像，然后等待输出结果即可。

<p align="center">开始检索</p>
<p align="center"><img src="https://github.com/GaryVillzoy/Content-based-Image-Retrieval/blob/master/README_images/4.png"  height = 250 width = 300 alt="search result"/></p>

5. 检索结果可直接在用户界面下方看到。排名从高到低会从左到右输出，并且输出此次检索的用时。如果用户选择的返回结果图片数大于3，则结果会通过弹窗的方式显示。

<p align="center">返回结果</p>
<p align="center"><img src="https://github.com/GaryVillzoy/Content-based-Image-Retrieval/blob/master/README_images/5.png"  height = 200 width = 500 alt="search result"/></p>

6. 在用户界面最下方可以选择数据集，并点击$$Calculate$$按钮计算数据集在该系统下的$$mAP$$。

<p align="center">计算mAP</p>
<p align="center"><img src="https://github.com/GaryVillzoy/Content-based-Image-Retrieval/blob/master/README_images/6.png"  height = 35 width = 400 alt="search result"/></p>
