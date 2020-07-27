<center><h1>Scripts to convert Annotations from one format to other formats. Specifically from .xml files to .TFRecords format.</h1></center>

You can have a look at example folder to get some understanding about it's working.

![](diagram.svg)

## A brief about Scripts

* **generate_csv.py** reads the contents of image annotations stored in [XML files](example/xml), created with [labelImg](https://github.com/tzutalin/labelImg), and generates a single [CSV file](example/output_test.csv).
* **generate_pbtxt.py** reads the previously generated CSV file (or any CSV file that has a column named _"class"_) or a text file containing a single class name per line and no header, and generates a [label map](example/output_test2.pbtxt), one of the files needed to train a detection model using [TensorFlow's Object Detection API](https://github.com/tensorflow/models/tree/master/research/object_detection).
* **generate_tfrecord.py** reads the previously generated CSV and label map files, as well as all the images from a given directory, and generates a TFRecord file, which can then be used to train an object detection model with TensorFlow. The resulting TFRecord file is about the same size of all the original images that were included in it.
* **generate_yolo_txt.py** reads the CSV file and generates one .txt file for each image mentioned in the CSV file, whith the same name of the image file. These .txt files contain the object annotations for that image, in a format which [darknet](https://pjreddie.com/darknet/yolo/) uses to train its models.

## How to Use
There is no hard and fast rule to use it. You just have to fork it and run the given .ipynb file in google colab. But before using it upload your xml files and it's corresponding images to the the drive which you'll be mounting with the colab notebook. Store the images and corresponding .xml files in separate folders.
