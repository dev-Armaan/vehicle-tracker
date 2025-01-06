# :car: :camera_flash: Vehicle Tracker

This model performs speed estimation analysis using technologies such as YOLO, OpenCV and argparse. It also uses the supervision package for multiple tasks such as tracking, annotations, etc.

The model calculates the instantenous speed of passing vehicles as well as counts the number of vehicles that pass over the duration of the input video. Additionally, it differentiates between semis/trucks (in green) and cars (in peach) for more comprehensive traffic analysis.

NOTE: Adjust the `SOURCE` and `TARGET` configuration if you plan to run a speed estimation script on your video file. Those must be adjusted separately for each camera view.


## Demo

https://github.com/user-attachments/assets/0d9fdb1b-6349-4604-8cd0-6e549e4e8978


Click [here](https://youtu.be/S-3mQ_zNbvw) to see a longer video of the model in action. The demo uses US Interstate Highway footage and compares the raw vs. processed footage side-by-side.

## :computer: Installation

* clone repo
```bash
git clone https://github.com/dev-Armaan/vehicle-tracker
```

* install required dependencies
```bash
pip install -r requirements.txt
```

* download `vehicles.mp4` file
```bash
python3.11 video_downloader.py
```

## :wrench: Script Arguments

`source_weights_path:` Required. Specifies the path to the YOLO model's weights file, which is essential for the object detection process. This file contains the data that the model uses to identify objects in the video.

`source_video_path:` Required. The path to the source video file that will be analyzed. This is the input video on which traffic flow analysis will be performed.

`target_video_path:` Required. The path to save the output video with annotations. If not specified, the processed video will be displayed in real-time without being saved.

`confidence_threshold (optional):` Sets the confidence threshold for the YOLO model to filter detections. Default is 0.3. This determines how confident the model should be to recognize an object in the video.

`iou_threshold (optional):` Specifies the IOU (Intersection Over Union) threshold for the model. Default is 0.7. This value is used to manage object detection accuracy, particularly in distinguishing between different objects.

## :runner: Run

```bash
python ultralytics_script.py \
    --source_video_path data/vehicles.mp4 \
    --target_video_path data/vehicles-result.mp4 \
    --confidence_threshold 0.3 \
    --iou_threshold 0.5
```

## :copyright: Licenses

This project integrates two main components, each with its own licensing:

ultralytics: The object detection model used here, YOLOv8, is distributed under the [AGPL-3.0 license](https://github.com/ultralytics/ultralytics/blob/main/LICENSE).

supervision: The analytics code that powers the zone-based analysis in this demo is based on the Supervision library, which is licensed under the [MIT license](https://github.com/roboflow/supervision/blob/develop/LICENSE.md).



