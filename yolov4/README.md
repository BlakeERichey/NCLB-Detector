1. obj.names  
  This is a file that specifies the classes in our custom classifier deliminated
  a new line (each class is on a new line). 
  In our model, we only have one class - Diseased which darknet will interpet to 
  be class_id 0.

2. obj.data  
  This file contains important info for darknet that instructs the framework 
  where to find train/test data, class names, how many classes the network 
  should be trained on, and where to backup intermediate model checkpoints.

3. train.txt 
  A list of image filenames for training our model on.

4. test.txt
  A list of image filenames to test our model against.

5. yolov4-nclb_best.weights  
  A file containing the optimal weights during training.  

6. yolov4-nclb.cfg  
  A file containing the architecture configuration for our YoloV4 model for detecting 
  Northern Corn Leaf Blight.  

7. yolov4.conv.137  
  A weights file for leveraging transfer learning when training custom models. 
  Pretrained on MSCOCO.

train.txt, test.txt, and their corresponding samples are generated via 
`scripts/gen_corn_samples.ipynb`.