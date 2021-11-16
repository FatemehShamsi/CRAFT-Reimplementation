
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

### Train for Persian data based on IC17
We also trained the model for the Persian language.

first we create Persian synthetic data sets accordance to the https://arxiv.org/pdf/1604.06646.pdf , then we trained the model with that.

Due to the lack of Persian data sets to train the model with real data, we produced our own personal data set, which includes 400 images for training and 100 images for testing. Then we trained the model with this data set.[Persian data set](https://drive.google.com/file/d/13aqZQWXsl2aL7mVRFvvGTBlYwl-VSe5n/view?usp=sharing)

Also, due to the fact that some letters in Persian are stuck together, we changed the following constants.
- text_threshold=0.6.
- low_text=0.5.
- link_threshold=0.3.

Here are some examples of test images.

![](https://github.com/FatemehShamsi/CRAFT-Reimplementation/blob/master/image/114.jpg)

![](https://github.com/FatemehShamsi/CRAFT-Reimplementation/blob/master/image/res_114_mask_on_image.jpg)

![](https://github.com/FatemehShamsi/CRAFT-Reimplementation/blob/master/image/156.jpg)

![](https://github.com/FatemehShamsi/CRAFT-Reimplementation/blob/master/image/res_156_mask_on_image.jpg)



