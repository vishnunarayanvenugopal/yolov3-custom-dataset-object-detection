# YOLOV3 #google_collab

#note : Intially we are going to implement on YOLO V3 and not YOLO_tiny.We will describe steps to use YOLO_tiny later in the same tutorial.

Installation of YOLO V3 and object detection using the same on our own custom data set.The following is done in Google collab https://colab.research.google.com/ . You can try the same in google collab.

### START WITH FOLLOWING RESOURCES (Download Following)

1. Download this github repository

### STEPS

1. Download Dataset (images of objects you want to detect)
2. Label the Data
3. Merge text output and image file input to one folder

#### 1.Download Dataset

Download as much of images of the object you want to detect using YOLO_V3. More the images, more the accuracy.You can download the dataset if its available as it is or you may download individually from google or other sources.

Save all these images to YOLOV3/data_label/main/input

There is a collection of cars and vehicle images in the folder because we want to detect vehicles.

![Image of Dataset_input](https://github.com/vichuroxx/YOLOV3/blob/master/img/2%20.%20data_input.JPG)

#### 2.Label Data

Open the class_list.txt file in the YOLOV3/data_label/main/. In the text file edit and add the classes. For example we need to identify 9 classes, car ,bus,person,bike,auto,van,cycle etc. Add this line by line

![Class list](https://github.com/vichuroxx/YOLOV3/blob/master/img/1.%20class_list.JPG)

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

![cmd](https://github.com/vichuroxx/YOLOV3/blob/master/img/4%20.%20cmd.JPG)

Now a window will open up and in which you can label each object.controls are as follows
D - next image
A - Previous image
W - next label
S - previous label

![label](https://github.com/vichuroxx/YOLOV3/blob/master/img/5%20.%20label.JPG)

Label all images. The YOLOV3\data_label\main\output\YOLO_darknet will now contain text files corresponding to each images.This stores our label. We have now successfully labelled our data.

![Output_text_files](https://github.com/vichuroxx/YOLOV3/blob/master/img/3%20.%20data_output.JPG)

#### 3. Merge text output and image file input to one folder



