# JetRacer Object Following

![alt text](https://github.com/sanem2000/JetRacer-Soccer-League/blob/main/Videos/Pictures/object_following.gif)

This section contains our attempt to train JetRacer to recognize the target object (the soccer ball) and steer in the appropriate direction based on the position of the object in the frame. 

## Setup:

1. For object detection, in this section we have used the tiny-yolo model of Yolov4. To try to train by yourself, please follow the excellent tutorial provided in the darknet github page referenced below.
2. To try out our implementation, please download all the files provided in this link and place it in a folder of your choice.
3. Also, please make sure you are using OpenCV version > 4.5

## Implementation:

Please check out **object_following.ipynb** for our implementation

## References:

1. https://github.com/NVIDIA-AI-IOT/jetbot/tree/master/notebooks/object_following
2. https://github.com/NVIDIA-AI-IOT/jetracer
3. https://github.com/AlexeyAB/darknet
4. https://pyimagesearch.com/2018/11/12/yolo-object-detection-with-opencv/
