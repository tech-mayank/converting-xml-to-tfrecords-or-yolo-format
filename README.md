<center><h1>Scripts to convert Annotations from one format to other formats. Specifically from .xml files to .TFRecords format.</h1></center>

You can have a look at example folder to get some understanding about it's working.

![](diagram.svg)

## Scripts

* **generate_csv.py** reads the contents of image annotations stored in [XML files](examples/xml), created with [labelImg](https://github.com/tzutalin/labelImg), and generates a single [CSV file](examples/output_test.csv).
* **generate_pbtxt.py** reads the previously generated CSV file (or any CSV file that has a column named _"class"_) or a text file containing a single class name per line and no header, and generates a [label map](examples/label_map.pbtxt), one of the files needed to train a detection model using [TensorFlow's Object Detection API](https://github.com/tensorflow/models/tree/master/research/object_detection).
* **generate_tfrecord.py** reads the previously generated CSV and label map files, as well as all the images from a given directory, and generates a TFRecord file, which can then be used to train an object detection model with TensorFlow. The resulting TFRecord file is about the same size of all the original images that were included in it.
* **generate_yolo_txt.py** reads the CSV file and generates one .txt file for each image mentioned in the CSV file, whith the same name of the image file. These .txt files contain the object annotations for that image, in a format which [darknet](https://pjreddie.com/darknet/yolo/) uses to train its models.

## Usage

The scripts are to be called in a terminal. In order to know what arguments a particular script expects, run it with the `-h` flag to see a help message. For example: `python generate_tfrecord.py -h`

#
