# AGE_ESTIMATION_PROJECT
Personal project for predicted age using Tensorflow, Keras, base on research paper. Using Mean-Variance Loss and Softmax Loss to predict age.

In this project, I build a model base on ResNet-34 architecture.
Update: Using pretrained model return a better result, in this case i use InceptionV3

## * NEW BIG UPDATE Aug-2021
* Adding PyTorch implementation
* Using model ResNet50 pretrained on ImageNet
* Define a full pipeline training and tracking experiment
* Train on another datatset which is called All-Age-Face dataset contain more than 13000 face images mostly from Asia
* Using Weight and Bias to track the experiment and log images and metric data

## THEORY
When doing age estimate we often choose between Softmax loss or L2 loss, if we use Sofmax loss it become a classification problem, and if we use L2 loss it is a regression problem. Both solutions have a issue is that they do not model the ordinal relationship between different age. For us human, we give an age estimate with a particular confidence interval, such as a Gaussian distribution with a particular mean age and a standard deviation. From this observation, the authors proposed Mean-Variance Loss which use to penalize the mean of estimated age distribution and the groundtruth age and also make the distrbution as sharp as posible by penalize the variance of age distribution.



## DATASET
The dataset i'm using is FG-NET dataset, which has 1002 images of people between 0-69 years old.
Link: http://yanweifu.github.io/FG_NET_data/FGNET.zip

Download All-Age-Face dataset from this repo [Download](https://github.com/JingchunCheng/All-Age-Faces-Dataset)
## RESULT
![Image](https://github.com/duylebkHCM/AGE_ESTIMATION_PROJECT/blob/master/assets/Screenshot%20from%202020-05-20%2022-08-45.png)
![Image](https://github.com/duylebkHCM/AGE_ESTIMATION_PROJECT/blob/master/assets/Screenshot%20from%202020-05-20%2022-08-48.png)

# REFERENCE
H. Pan, H. Han, S. Shan and X. Chen, "Mean-Variance Loss for Deep Age Estimation from a Face," 2018 IEEE/CVF Conference on Computer Vision and Pattern Recognition, Salt Lake City, UT, 2018, pp. 5285-5294, doi: 10.1109/CVPR.2018.00554.
