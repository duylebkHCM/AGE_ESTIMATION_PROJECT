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

<img src="https://github.com/duylebkHCM/AGE_ESTIMATION_PROJECT/blob/master/assets/oveview.png" alt="ov" width=900 />
For yi denote age class, j also class label, pi denotes the estimated age distribution for sample i over all the K classes, and pi, j denotes the probability that sample i belongs to class j. We have:

<p align="center">
<img src="https://github.com/duylebkHCM/AGE_ESTIMATION_PROJECT/blob/master/assets/m_loss.png" alt="m_l" width=400 />
<img src="https://github.com/duylebkHCM/AGE_ESTIMATION_PROJECT/blob/master/assets/v_loss.png" alt="v_l" width=400 />
</p>

## DATASET
The dataset i'm using is FG-NET dataset, which has 1002 images of people between 0-69 years old.
Link: http://yanweifu.github.io/FG_NET_data/FGNET.zip

Download All-Age-Face dataset from this repo [Download](https://github.com/JingchunCheng/All-Age-Faces-Dataset)

## INSTRUCTION
* For TensorFlow ver, checkout [this notebook](https://github.com/duylebkHCM/AGE_ESTIMATION_PROJECT/blob/master/Age_Estimation_v2.ipynb)
* For PyTorch ver, if you want to train FG-Net dataset first you need to preprocess this dataset by using [this notebook](https://github.com/duylebkHCM/AGE_ESTIMATION_PROJECT/blob/master/PREPROCESS_FACE.ipynb), and then inside [this notebook](https://github.com/duylebkHCM/AGE_ESTIMATION_PROJECT/blob/master/Age_Estimation_PyTorch.ipynb) has detail instruction; if you want to train ALL-AGE-FACE dataset just use [this notebook](https://github.com/duylebkHCM/AGE_ESTIMATION_PROJECT/blob/master/Age_Estimation_PyTorch_on_ALL_AGE_FACE.ipynb)
* Note: to use Wandb you first need to create an account

## RESULT
I use cross-validation with 5 folds for FG-Net and 3 folds for AAF. **On FG-Net mean MAE on 5 folds is 4.482, on AAF mean MAE on 3 folds is 5.517**
<p align="center">
<img src="https://github.com/duylebkHCM/AGE_ESTIMATION_PROJECT/blob/master/assets/fnet_tloss.png" alt="fnet_tloss" width=800 />
</p>

<p align="center">
<img src="https://github.com/duylebkHCM/AGE_ESTIMATION_PROJECT/blob/master/assets/fnet_tloss.png" alt="fnet_tloss" width=800 />
</p>

### * Some predicted images on FG-NET
<p align="center">
<img src="https://github.com/duylebkHCM/AGE_ESTIMATION_PROJECT/blob/master/assets/fnet_f1.png" alt="fnet_f1" width=600 />
<img src="https://github.com/duylebkHCM/AGE_ESTIMATION_PROJECT/blob/master/assets/fnet_f2.png" alt="fnet_f2" width=600 />
<img src="https://github.com/duylebkHCM/AGE_ESTIMATION_PROJECT/blob/master/assets/fnet_f3.png" alt="fnet_f3" width=600 />
<img src="https://github.com/duylebkHCM/AGE_ESTIMATION_PROJECT/blob/master/assets/fnet_f4.png" alt="fnet_f4" width=600 />
<img src="https://github.com/duylebkHCM/AGE_ESTIMATION_PROJECT/blob/master/assets/fnet_f5.png" alt="fnet_f5" width=600 />
</p>

### * Some predicted images on AAF
<p align="center">
<img src="https://github.com/duylebkHCM/AGE_ESTIMATION_PROJECT/blob/master/assets/aaf_f1.png" alt="aaf_f1" width=600 />
<img src="https://github.com/duylebkHCM/AGE_ESTIMATION_PROJECT/blob/master/assets/aaf_f2.png" alt="aaf_f2" width=600 />
<img src="https://github.com/duylebkHCM/AGE_ESTIMATION_PROJECT/blob/master/assets/aaf_f3.png" alt="aaf_f3" width=600 />
</p>

### Other images
![Image](https://github.com/duylebkHCM/AGE_ESTIMATION_PROJECT/blob/master/assets/Screenshot%20from%202020-05-20%2022-08-45.png)
![Image](https://github.com/duylebkHCM/AGE_ESTIMATION_PROJECT/blob/master/assets/Screenshot%20from%202020-05-20%2022-08-48.png)

# REFERENCE
H. Pan, H. Han, S. Shan and X. Chen, "Mean-Variance Loss for Deep Age Estimation from a Face," 2018 IEEE/CVF Conference on Computer Vision and Pattern Recognition, Salt Lake City, UT, 2018, pp. 5285-5294, doi: 10.1109/CVPR.2018.00554.
