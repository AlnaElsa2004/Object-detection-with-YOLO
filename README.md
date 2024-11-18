# YOLO Object Detection Using Darknet

This repository contains the necessary steps to set up YOLO (You Only Look Once) object detection using the Darknet framework. The following guide will help you clone the repository, run object detection on both images and videos, and adjust settings like threshold and `ext_output` for enhanced results.

## Steps to Run YOLO with Darknet

### 1. Clone the Darknet Repository

First, clone the Darknet repository from GitHub:

```bash
git clone https://github.com/AlexeyAB/darknet
cd darknet
```
### 2. Build Darknet

After cloning the repository and installing dependencies, you need to build Darknet by compiling it. Run:

```bash
make
```

### 3. Download YOLO Pre-trained Weights

To use YOLO for object detection, you need the pre-trained weights. Download the YOLOv4 weights file using the following command:

```bash
wget https://github.com/AlexeyAB/darknet/releases/download/yolov4/yolov4.weights
```

### 4. Detecting Objects in Images

To run object detection on a single image, use the following command:

```bash
./darknet detect cfg/yolov4.cfg yolov4.weights data/dog.jpg
```
This will load the image `dog.jpg` from the `data` folder, perform object detection, and save the result to `predictions.jpg`.

You can replace `data/dog.jpg` with your own image path.

#### Adjusting the Threshold

The threshold is the minimum confidence required to detect an object. You can adjust it to filter low-confidence detections. By default, it is set to 0.24, but you can change it as follows:

```bash
./darknet detect cfg/yolov4.cfg yolov4.weights data/dog.jpg -thresh 0.5
```
This will use a threshold of 0.5 (50% confidence).

#### Using ext_output

To print additional output about the detected objects, including the class name and confidence score, use the -ext_output flag:

```bash
./darknet detect cfg/yolov4.cfg yolov4.weights data/dog.jpg -ext_output
```

### 5. Detecting Objects in Videos

To detect objects in a video, use the following command:

```bash
./darknet detector demo cfg/coco.data cfg/yolov4.cfg yolov4.weights <video_path>
```

### 6. Output

For both image and video detections, the results will be saved as predictions.jpg or displayed in the video. The output image/video will include bounding boxes around the detected objects.

## License

This project is licensed under the MIT License - see the `LICENSE` file for details.
