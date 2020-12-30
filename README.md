# Yolov5-Torch
Pytorch implementation of Yolov5 

# Requirements
Unzip all the compressed folder in the default work directory
pip install -r requirements.txt

But a little headsup, if you're on windows kindly install pytorch and it's dependencies prior to running the above command. 

# Download weights
Use download_weights.py and download the weights for the following pre-built variants of yolov5: 5l,5m,5s,5x... s being the smallest

# Steps to run the system smoothly

Examples:
Path_to_the_data = D:/Object Detection/yolov5/data/pothole/data.yaml # In different directory 
Path_to_the_data = data/railway_line/data.yaml # Same Directory 

python train.py --img 640 --batch 4 --epochs 60 --data Path_to_the_data --weights yolov5s.pt --nosave --cache
python train.py --img 640 --batch 4 --epochs 70 --data Path_to_the_data --weights yolov5s.pt --nosave --cache


python detect.py --source   0  # webcam
                            file.jpg  # image 
                            file.mp4  # video
                            path/  # directory
                            path/*.jpg  # glob
                            rtsp://170.93.143.139/rtplive/470011e600ef003a004ee33696235daa  # rtsp stream
                            rtmp://192.168.1.105/live/test  # rtmp stream
                            http://112.50.243.8/PLTV/88888888/224/3221225900/1.m3u8  # http stream

python detect.py --source data/images --weights yolov5s.pt --conf 0.25 #Data folder comprising of images

python detect.py --source vid_rail.mp4 --weights yolov5s.pt --conf 0.25 #Working directory comprising of data

python detect.py --weights  runs/train/exp17/weights/last.pt --source data/thermal_dogs_people/test/images/ --view-img

python detect.py --weights  runs/train/exp18/weights/last.pt --source data/wild_fire_smoke/test/images/ --view-img

python detect.py --weights  runs/train/exp20/weights/last.pt --source data/railway_line/test/images/ --view-img

python detect.py --weights  runs/train/exp21/weights/last.pt --source data/railway_line/test/images/ --view-img


python detect.py --weights  runs/train/exp21/weights/last.pt --source data/railway_line/non-defect/ --view-img

The outputs from train and detection are stored in the runs folder

# Comverting Torch models to Onnx
python models/export.py --weights runs/train/exp18/weights/last.pt --img 640 --batch 1

# Flask API
python detect_api.py runs/train/exp18/weights/last.pt

python utils/client_api.py
