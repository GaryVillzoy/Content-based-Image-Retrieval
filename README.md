# Content-based Image Retrieval (CBIR) System

### I. Source Code Files

1. Open file `Content_based_Image_Retrieval.mlapp` in Matlab to display the user interface and view every function.
2. `cal_mAP_codes.rar` contains source code files used to calculate the mAP of the system. `getResultFile***128D` and `getResultFile***4096D` denote the retrieval ranking in the dimension of 128 and 4096, respectively, according to the official groundtruth files of the datasets used. `calMAP***128D.m` and `calMAP***4096D.m` are used to calculate the mAP of a dataset in 128 and 4096 dimensions, respectively, using the ranking obtained earlier.

### II. Model and Data Sets

1. `imagenet-vgg-f.mat` is a pre-trained model of the VGG network provided by MatConvNet and can be used directly.
2. The Data folder holds all the data files required by the program. `resultFile***---D.dat` presents the retrieval ranking of a dataset in the corresponding dimension based on its groundtruth file,. `***FeaturesNorm.mat` stores the feature vectors of all the images of a dataset in the dimension of 4096, while `***128D.mat` stores that in the dimension of 128. `gnd_Oxford.mat` is the groundtruth file for the Oxford5k dataset. `holidays_images.dat` is also the official file for calculating the mAP of the Holidays dataset.

### III. User Guide

1. First, users are required to choose a model for the image retrieval later. Click "Select A Model" to select the model file, i.e., `imagenet-vgg-f.mat`.

<p align="center">Select your model</p>
<p align="center"><img src="https://github.com/GaryVillzoy/Content-based-Image-Retrieval/blob/master/README_images/1.png"  width = 400 alt="search result"/></p>

2. Then users need to answer the following questions, that is, whether MatConvNet has been compiled and whether the dataset that will be selected is a mat file (i.e., whether the image dataset has been feature-extracted). If the network has not been compiled, then the system will automatically compile it afterwards, but it will take a while. If the dataset is not feature-extracted, the system will automatically perform feature extraction after selecting the image dataset, which also consumes some time.

   <p align="center">Answer some questions</p>
   <p align="center"><img src="https://github.com/GaryVillzoy/Content-based-Image-Retrieval/blob/master/README_images/2.png"  width = 400 alt="search result"/></p>

3. After that, users can select the dataset for image retrieval. If the dataset is a mat file, the proposed system automatically determines the dimension of the data based on the file name. Otherwise, the "Extract features" button will be available, and users are required to manually select the dimension of features.

   <p align="center">Import the dataset</p>
   <p align="center"><img src="https://github.com/GaryVillzoy/Content-based-Image-Retrieval/blob/master/README_images/3.png"  width = 400 alt="search result"/></p>

4. Eventually, users can perform image retrieval. Users can select the number of images to be retrieved by adjusting "Retrieval Number", then click "Start retrieval" button to select the source images. 

<p align="center">Perform retrieval</p>
<p align="center"><img src="https://github.com/GaryVillzoy/Content-based-Image-Retrieval/blob/master/README_images/4.png"  height = 250 width = 300 alt="search result"/></p>

5. Generally, the retrieval result will be display on the bottom of the user interface. The images are placed in a descending order of similarity. The query time is also presented. If the number of images to be retrieved is greater than 3, the results will be displayed via a pop-up window.

<p align="center">Display results</p>
<p align="center"><img src="https://github.com/GaryVillzoy/Content-based-Image-Retrieval/blob/master/README_images/5.png"  height = 200 width = 500 alt="search result"/></p>

6. User can also calculate the mAP of a given dataset. 

<p align="center">Calculate mAP</p>
<p align="center"><img src="https://github.com/GaryVillzoy/Content-based-Image-Retrieval/blob/master/README_images/6.png"  height = 35 width = 400 alt="search result"/></p>

### IV. Cautions

1. Be sure to check out the MatConvNet toolbox in advance.

2. Please download the pre-training model from the official website first. The pre-training model used in this system is `imagenet-vgg-f.mat`.
