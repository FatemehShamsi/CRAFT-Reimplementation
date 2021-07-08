
## Reimplementation：Character Region Awareness for Text Detection Reimplementation based on Pytorch

## Character Region Awareness for Text Detection
Youngmin Baek, Bado Lee, Dongyoon Han, Sangdoo Yun, Hwalsuk Lee
(Submitted on 3 Apr 2019)

The full paper is available at: https://arxiv.org/pdf/1904.01941.pdf                                                         

## Install Requirements:                                                                                                        
1、PyTroch>=0.4.1                                                                                                                             
2、torchvision>=0.2.1 			                                                    																			                             
3、opencv-python>=3.4.2                                                                                                       
4、check requiremtns.txt                                                                                                      
5、4 nvidia GPUs(we use 4 nvidia titanX)                                                                                      


## pre-trained model:
`NOTE: There are old pre-trained models, I will upload the new results pre-trained models' link.`                                                                                
Syndata:[Syndata for baidu drive](https://pan.baidu.com/s/1MaznjE79JNS9Ld48ZtRefg) ||     [Syndata for google drive](https://drive.google.com/file/d/1FvqfBMZQJeZXGfZLl-840YXoeYK8CNwk/view?usp=sharing)                                                                                                    
Syndata+IC15:[Syndata+IC15 for baidu drive](https://pan.baidu.com/s/19lJRM6YWZXVkZ_aytsYSiQ) ||      [Syndata+IC15 for google
 drive](https://drive.google.com/file/d/1k17GuBG_omT91tJoIMSlLrorYbLXkq4z/view?usp=sharing)                                   
 Syndata+IC13+IC17:[Syndata+IC13+IC17 for baidu drive](https://pan.baidu.com/s/1PTTzbM9XG0pNe5i-uL6Aag)||      [Syndata+IC13+IC17 for google drive](https://drive.google.com/open?id=1SkJEfaGYIq-eFxfzFVZb-cGdGWR8lPSi) 


## Training 
`Note: When you train the IC15-Data or MLT-Data, please see the annotation in data_loader.py line 92 and line 108-112.`

### Train for Syndata
- download the Syndata(I will give the link)
- change the path in basernet/vgg16_bn.py file:
>` (/data/CRAFT-pytorch/vgg16_bn-6c64b313.pth -> /your_path/vgg16_bn-6c64b313.pth).You can download the model here.`[baidu](https://pan.baidu.com/s/1_h5qdwYQAToDi_BB5Eg3vg)||[google](https://drive.google.com/open?id=1ZtvGpFQrbmEisB_GhmZb8UQOtvqY_-tW)                                                                 
- change the path in trainSyndata.py file:
> `(1、/data/CRAFT-pytorch/SynthText -> /your_path/SynthText 2、/data/CRAFT-pytorch/synweights/synweights -> /your_path/real_weights)`                                                                      
- Run **`python trainSyndata.py`**

### Train for IC15 data based on Syndata pre-trained model
- download the IC15 data, rename the image file and the gt file for  ch4_training_images and ch4_training_localization_transcription_gt,respectively.
- change the path in basernet/vgg16_bn.py file:                                                                                                                                                              
> `(/data/CRAFT-pytorch/vgg16_bn-6c64b313.pth -> /your_path/vgg16_bn-6c64b313.pth).You can download the model here.`[baidu](https://pan.baidu.com/s/1_h5qdwYQAToDi_BB5Eg3vg)||[google](https://drive.google.com/open?id=1ZtvGpFQrbmEisB_GhmZb8UQOtvqY_-tW)
- change the path in trainic15data.py file:                                                                                                                                                                  
>` (1、/data/CRAFT-pytorch/SynthText -> /your_path/SynthText    2、/data/CRAFT-pytorch/real_weights -> /your_path/real_weights)`
- change the path in trainic15data.py file:                                                                                                                                                                 
> `(1、/data/CRAFT-pytorch/1-7.pth -> /your_path/your_pre-trained_model_name 2、/data/CRAFT-pytorch/icdar1317 -> /your_ic15data_path/)`
- Run **`python trainic15data.py`**

### Train for IC13+17 data based on Syndata pre-trained model

- download the MLT data, rename the image file and the gt file,respectively.
- change the path in basernet/vgg16_bn.py file:                                                                                                                                                              
> `(/data/CRAFT-pytorch/vgg16_bn-6c64b313.pth -> /your_path/vgg16_bn-6c64b313.pth).You can download the model here.`[baidu](https://pan.baidu.com/s/1_h5qdwYQAToDi_BB5Eg3vg)||[google](https://drive.google.com/open?id=1ZtvGpFQrbmEisB_GhmZb8UQOtvqY_-tW)
- change the path in trainic-MLT_data.py file:                                                                                                                                                              
>` (1、/data/CRAFT-pytorch/SynthText -> /your_path/SynthText    2、savemodel path-> your savemodel path)`
- change the path in trainic-MLT_data.py file:                                                                                                                                                         
> `(1、/data/CRAFT-pytorch/1-7.pth -> /your_path/your_pre-trained_model_name 2、/data/CRAFT-pytorch/icdar1317 -> /your_ic15data_path/)`
- Run **`python trainic-MLT_data.py`**

### If you want to train for weak supervised use our Syndate pre-trained model:                                                                                                                                
1、You should first download the pre_trained model trained in the Syndata [baidu](https://pan.baidu.com/s/1MaznjE79JNS9Ld48ZtRefg)||[google](https://drive.google.com/file/d/1FvqfBMZQJeZXGfZLl-840YXoeYK8CNwk/view?usp=sharing).                                                                                                                                                      
2、change the data path and pre-trained model path.                                                                                                                                                         
3、run `python trainic15data.py`                                                                                                                                                                           

                                                                                                                    
**This code supprts for Syndata and icdar2015, and we will release the training code for IC13 and IC17 as soon as possible.**

Methods                                       |dataset      |Recall      |precision      |H-mean
----------------------------------------------|-------------|------------|---------------|------
Syndata                                       |ICDAR13      |71.93%      |81.31%         |76.33%                                                                          
Syndata+IC15                                  |ICDAR15      |76.12%      |84.55%         |80.11%               
Syndata+MLT(deteval)                          |ICDAR13      |86.81%      |95.28%         |90.85%                                   
Syndata+MLT(deteval)(new gaussian map method) |ICDAR13      |90.67%      |94.56%         |92.57%                                   
Syndata+IC15(new gaussian map method)         |ICDAR15      |80.36%      |84.25%         |82.26%


### Train for Persian data based on IC17
We also trained the model for the Persian language.

first creat Persian synthetic data sets accordance to the https://arxiv.org/pdf/1604.06646.pdf , then trained model.

Due to the lack of Persian data set to train the model with real data, we produced our own personal data set, which includes 400 images for training and 100 images for testing. Then we trained the model with this data set.[Persian data set](https://drive.google.com/file/d/13aqZQWXsl2aL7mVRFvvGTBlYwl-VSe5n/view?usp=sharing)

Also, due to the fact that some letters in Persian are stuck together, we changed the following constants.

Here are some examples of test images.

![](https://github.com/FatemehShamsi/CRAFT-Reimplementation/blob/master/image/114.jpg)

![](https://github.com/FatemehShamsi/CRAFT-Reimplementation/blob/master/image/res_114_mask_on_image.jpg)

![](https://github.com/FatemehShamsi/CRAFT-Reimplementation/blob/master/image/156.jpg)

![](https://github.com/FatemehShamsi/CRAFT-Reimplementation/blob/master/image/res_156_mask_on_image.jpg)



