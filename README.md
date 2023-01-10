# ONNX YOLOv8 Object Detection
 Python scripts performing object detection using the YOLOv8 model in ONNX.

![! ONNX YOLOv8 Object Detection](https://github.com/ibaiGorordo/ONNX-YOLOv8-Object-Detection/blob/main/doc/img/detected_objects.jpg)
*Original image: https://www.flickr.com/photos/nicolelee/19041780*

# Important
- The input images are directly resized to match the input size of the model. I skipped adding the pad to the input image, it might affect the accuracy of the model if the input image has a different aspect ratio compared to the input size of the model. Always try to get an input size with a ratio close to the input images you will use.

# Requirements

 * Check the **requirements.txt** file.
 * For ONNX, if you have a NVIDIA GPU, then install the **onnxruntime-gpu**, otherwise use the **onnxruntime** library.

# Installation
```
git clone https://github.com/ibaiGorordo/ONNX-YOLOv8-Object-Detection.git
cd ONNX-YOLOv8-Object-Detection
pip install -r requirements.txt
```
### ONNX Runtime
For Nvidia GPU computers:
`pip install onnxruntime-gpu`

Otherwise:
`pip install onnxruntime`

# ONNX model
You can conver the model using the following code after installing ultralitics (`pip install ultralytics`):
```
from ultralytics import YOLO

model = YOLO("yolov8m.pt") 
model.export(format="onnx", imgsz=[480,640])
```
The original models were converted to different formats (including .onnx) by [PINTO0309](https://github.com/PINTO0309). Download the models from **[his repository]**(https://github.com/PINTO0309/PINTO_model_zoo/tree/main/345_YOLOv8). For that, you can either run the `download_single_batch.sh` or copy the download link inside that script in your browser to manually download the file. Then, extract and copy the downloaded onnx models (for example `yolov8m_480x640.onnx`) to your **[models directory](https://github.com/ibaiGorordo/ONNX-YOLOv8-Object-Detection/tree/main/models)**, and fix the file name in the python scripts accordingly.

# Original YOLOv8 model
The original YOLOv8 model can be found in this repository: [YOLOv8 Repository](https://github.com/ultralytics/ultralytics)
- The License of the models is GPL-3.0 license: [License](https://github.com/ultralytics/ultralytics/blob/main/LICENSE)

# Examples

 * **Image inference**:
 ```
 python image_object_detection.py
 ```

 * **Webcam inference**:
 ```
 python webcam_object_detection.py
 ```

 * **Video inference**: https://youtu.be/yYo0XQp97vo
 ```
 python video_object_detection.py
 ```

[//]: # ( ![!YOLOv8 detection video]&#40;https://github.com/ibaiGorordo/ONNX-YOLOv8-Object-Detection/blob/main/doc/img/yolov8_video.gif&#41;)

[//]: # (  *Original video: https://youtu.be/zPre8MgmcHY*)

# References:
* YOLOv8 model: https://github.com/ultralytics/ultralytics
* YOLOv5 model: https://github.com/ultralytics/yolov5
* YOLOv6 model: https://github.com/meituan/YOLOv6
* YOLOv7 model: https://github.com/WongKinYiu/yolov7
* PINTO0309's model zoo: https://github.com/PINTO0309/PINTO_model_zoo
* PINTO0309's model conversion tool: https://github.com/PINTO0309/openvino2tensorflow