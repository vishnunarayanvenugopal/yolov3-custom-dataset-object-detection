# YOLOV3 #google_collab

#note : Intially we are going to implement on YOLO V3 and not YOLO_tiny.We will describe steps to use YOLO_tiny later in the same tutorial.

Installation of YOLO V3 and object detection using the same on our own custom data set.The following is done in Google collab https://colab.research.google.com/ . You can try the same in google collab.

![Output image](https://github.com/vichuroxx/YOLOV3/blob/master/img/out.png)

### START WITH FOLLOWING RESOURCES (Download Following)

1. Download this github repository : https://github.com/vichuroxx/YOLOV3-Custom-dataset-Object-detection
2. Download this collab file : https://github.com/vichuroxx/YOLOV3-Custom-dataset-Object-detection/blob/master/YoloV3.ipynb

### STEPS

1. Download Dataset (images of objects you want to detect)
2. Label the Data
3. Merge text output and image file input to one folder
4. Train & Test file generation
5. Anchor Calculation
6. Prepare Data for collab folder
7. Run the collab file @ https://github.com/vichuroxx/YOLOV3-Custom-dataset-Object-detection/blob/master/YoloV3.ipynb

#### 1.Download Dataset

Download as much of images of the object you want to detect using YOLO_V3. More the images, more the accuracy.You can download the dataset if its available as it is or you may download individually from google or other sources.

Save all these images to YOLOV3/data_label/main/input

There is a collection of cars and vehicle images in the folder because we want to detect vehicles.

![Image of Dataset_input](https://github.com/vichuroxx/YOLOV3-Custom-dataset-Object-detection/blob/master/img/2%20.%20data_input.JPG)

#### 2.Label Data

Open the class_list.txt file in the YOLOV3/data_label/main/. In the text file edit and add the classes. For example we need to identify 9 classes, car ,bus,person,bike,auto,van,cycle etc. Add this line by line

![Class list](https://github.com/vichuroxx/YOLOV3-Custom-dataset-Object-detection/blob/master/img/1.%20class_list.JPG)

For labelling data we need to run a python program.This program requires the following to be installed in your PC or it will throw error.

lxml==4.3.0
numpy==1.16.0
opencv-contrib-python==3.4.5.20
tqdm==4.29.1

Run the program in cmd as administrator.

```
cd ../YOLOV3/data_label/main/input

python main.py
```

![cmd](https://github.com/vichuroxx/YOLOV3-Custom-dataset-Object-detection/blob/master/img/4%20.%20cmd.JPG)

Now a window will open up and in which you can label each object.controls are as follows
D - next image
A - Previous image
W - next label
S - previous label

![label](https://github.com/vichuroxx/YOLOV3-Custom-dataset-Object-detection/blob/master/img/5%20.%20label.JPG)

Label all images. The YOLOV3\data_label\main\output\YOLO_darknet will now contain text files corresponding to each images.This stores our label. We have now successfully labelled our data.

![Output_text_files](https://github.com/vichuroxx/YOLOV3-Custom-dataset-Object-detection/blob/master/img/3%20.%20data_output.JPG)

#### 3. Merge text output and image file input to one folder

Create a folder named data or any other and copy all the input images + output text file in the YOLOV3\data_label\main\output\YOLO_darknet together. it will look like the figure below.

![Merge Files](https://github.com/vichuroxx/YOLOV3-Custom-dataset-Object-detection/blob/master/img/6.%20merge.JPG)

#### 4. Train & Test file generation

Edit process.py and change path of current_dir = 'C:/Users/User/Desktop/project/vishnu/Yolo-Training-GoogleColab-master/data' to the location where data folder containing both text and image files are present.

Open train_test_conversion folder and execute process.py program. This is to split your input into training and testing set.

```
cd ..\YOLOV3\train_test_conversion

python process.py
```
Now the train.txt and test.txt files inside train_test_conversion folder will have splitted data.

#### 5. Anchor calculation

Open the anchors_calculation folder. Edit the anchors.py file and change the path of test.txt and  train.txt to yours that we have previously created. (at line 108 and 110). Edit output to your anchors folder path.

```
cd ..\YOLOV3\anchors_calculation

python anchors.py
```

Now open anchors6.txt file in the location ...\YOLOV3\anchors_calculation\anchors. It contains the anchor value. We need that value in our configuration file.

#### 6. Prepare Data for collab folder

* Replace the data folder with your data folder containing images and text files.
- Edit the obj.data file (enter the number of class no(car,bike etc) of objects to detect)
  - classes= 9  
  - train  = /content/darknet/data_for_colab/train.txt  
  - valid  = /content/darknet/data_for_colab/test.txt  
  - names = /content/darknet/data_for_colab/obj.names  
  - backup = backup/
- Edit obj.names files and list your classes line by line. In my clse (bike,car etc)
- copy the test.txt and train.txt files to here
- Now we have 3 other files, This is for YoloV3 and Yolo_tiny

download the file darknet53.conv.74 from the link  https://pjreddie.com/media/files/darknet53.conv.74 and add it to this folder.

darknet53.conv.74 & yolov3.cfg : YOLOV3
yolov3-tiny.conv.15 & yolov3-tiny-obj.cfg : YOLOV3_TINY

keep all the files, theres no issue.

- Edit the yolov3.cfg &  yolov3-tiny-obj.cfg files to change anchor,filters and class.

follow this for yolov3.cfg

https://github.com/AlexeyAB/darknet#how-to-train-to-detect-your-custom-objects 

follow this for yolov3-tiny-obj.cfg

  - edit the classes=[no of classes you have]
  - ![class](https://github.com/vichuroxx/YOLOV3-Custom-dataset-Object-detection/blob/master/img/7.%20classes.JPG)
  - edit the anchors=[anchors value in your generated file]
  - ![anchors](https://github.com/vichuroxx/YOLOV3-Custom-dataset-Object-detection/blob/master/img/8.%20anchors.JPG)
  - edit the filter=[calculate filter value from equation]
  - filter size=(num/3)*(classes+5) num is same as in .cfg file check for same
  - edit the filter values just above the anchors value (not all the filter values)
  - ![filters](https://github.com/vichuroxx/YOLOV3-Custom-dataset-Object-detection/blob/master/img/9.%20filter.JPG)
- Change path inside test.txt and train.txt from your path to google drive darknet path:  /content/darknet/data_for_colab/data/
  
Now compress the Data for collab folder to ZIP not RAR or any other format and upload to your google drive.

#### 6. Run collab file with run time assigned with GPU

![Output image](https://github.com/vichuroxx/YOLOV3-Custom-dataset-Object-detection/blob/master/img/out.png)


