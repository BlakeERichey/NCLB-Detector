# Overview  
This repo provides results presented in [this paper](https://www.spiedigitallibrary.org/conference-proceedings-of-spie/11736/1173606/Deep-learning-based-real-time-detection-of-northern-corn-leaf/10.1117/12.2587892.short?SSO=1) on 
detecting Northern Corn Leaf Blight in images.

# Dependencies  
1. Darknet  
    We train a neural network using the YoloV4 framework, which relies on darknet.
    Instruction to install darknet's dependencies can be found 
    [here](https://github.com/AlexeyAB/darknet#requirements-for-windows-linux-and-macos)  

2. Northern Corn Leaf Blight Dataset  
    We used a dataset documenting Northern Corn Leaf Blight that was procured 
    by Mohatney et al, which can be found [here](https://osf.io/p67rz/) in order 
    to train our neural network. 
    
    *Note: We specifically trained on a subset of the handheld data that *
    *contained only 1 instance of Northern Corn Leaf Blight in the image, *
    *to lessen the requirements of image augmentation.*  

# Training the custom model  

Instruction for training a YoloV4 model from scratch can be view on 
[colab](https://colab.research.google.com/drive/1_GdoqCJWXsChrOiY8sZMr_zbr_fH-0Fg) 
(aqcuired from YoloV4 documentation wiki).  

**All necessary yolov4 dependencies are provided in the yolov4 directory of this repo.**  

# Inference the model  

Download and configure darknet: 
```
git clone https://github.com/AlexeyAB/darknet
cd darknet
sed -i 's/OPENCV=0/OPENCV=1/' Makefile
sed -i 's/GPU=0/GPU=1/' Makefile
sed -i 's/CUDNN=0/CUDNN=1/' Makefile
sed -i 's/CUDNN_HALF=0/CUDNN_HALF=1/' Makefile
make
```

Run model on test data:
```
./darknet/darknet detector test yolov4/obj.data yolov4/yolov4-nclb.cfg yolov4/yolov4-nclb_best.weights demo/augmentations/00000050.jpg -thresh 0.3
```
