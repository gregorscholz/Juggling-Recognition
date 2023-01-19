# Juggling_Pattern_Recognition

# Introduction
The project provides juggling pattern recognition in either real-time or video format. This repository provides the real time balls detection and human pose estimation as well as common recognition of juggling **SITESWAP** notation from notation 1 to notation 8.

# Main Contents
* Utilized You-Only-Look-Once (YOLO) for ball detection.
* Utilized mediapipe for human pose estimation.
* Tensorflow framework to build a model for classification of juggling siteswap notation.
* Centroid tracking algorithm for object tracker.

# Getting Started (tested on Ubuntu 18.04 & Windows)
It is recommended to have tensorflow with GPU support for faster inference time (higher framerate) while running the program. Please do follow the installation step from NVIDIA to install CUDA and CUDNN into your system.

Please install the following necessary packages in python3.7 (or higher version) virtual environment:
* tensorflow-gpu/tensorflow-cpu (2.2.0 or higher)
* keras (2.3.1 or higher)
* mediapipe (0.8.9 or higher)
* pillow
* cv2
* numpy
* tkinter
* scikit-learn
* matplotlib


# Results and details
Output | Simulation
--- | ---
![](https://media.discordapp.net/attachments/709066676800323605/1065551049240358992/demo_image.png?width=1214&height=672) | ![](https://media.discordapp.net/attachments/709066676800323605/1065551048984510504/simulation_image.png?width=1199&height=672)
* **Output** result shows the detected balls that attached with specific ID and palm along with the data dashboard on the top right which displays the analysis of player performance.
* Balls with red bounding box covered is in unbound state which means its not being held in the hand.
* Balls with green bounding box covered is in bound state which means its held in the hand.
* **Simulation** result shows the human pose estimation along with the recognized pattern on the top left.
* Each recognized pattern is identified as the same color of the ball in the simulation result.
* Analysis result of ball in bound state will not be shown in data dashboard output result (since its grasped in hand hence height will be 0 as always) as well as will not be displayed in simulation result.
* The results will be stored in video files as output.avi and demo.avi (refer to videos below).

## Sample video results

https://drive.google.com/file/d/1W166MqkJuvYB1mTcX0Ra34P-YCeQ1qBT/view?usp=sharing


https://drive.google.com/file/d/1PlcUPAzM5WMJOYFflsaqf7EmHEWHDRwk/view?usp=sharing

# Instructions‼️‼️
1. A high quality camera is recommended to be used for capturing. You may also use phone camera or any external camera for better image quality hence improve the performance.
2. Please stand in a reasonable distance to camera, recommended 1-1.2 meter. The estimated distance is displayed in the data dashboard in output video.
3. Currently supports only balls juggling and not more than 3 balls.
4. Currently supports only siteswap notation 1 - 8 and some basic form of siteswap patterns, which variant of patterns are not recommended.
5. Please prevent same color between clothes, balls, and background (also light background).

# Scripts

## centroid tracking/
1. ```tracker.py```: Tracker class. Implemented centroid tracking algorithm and customized for this project usecase.
2. ```bound_tracking.py```: Tracking algoithm for bound object (balls).
3. ```classes.names```: YOLO class name.
4. ```config.py```: YOLO properties config file.

## core/
1. ```analysis.py```: Script for dashboard creation and the analysis of player's performance.
2. ```pattern.py```: Script for recognize siteswap notation/pattern.
3. ```posemodule.py```: Script for human pose estimation.
4. ```simulation.py```: Script for displaying the simulation frames along with the human pose, balls, and recognized siteswap notation/pattern.
5. ```utils.py```: Contains functions that will call the scripts above.

## pattern_recog_model_generator/
1. ```model_train.py```: Build model and training script.
2. ```pattern_model.h5```: Trained model.
3. ```data/x.npz```: X dataset.
4. ```data/y.npz```: Y dataset.

## src/
1. Contains all the testing videos used in this project.

## ./
1. ```main.py```: Main program script.
2. ```output.avi```: Output video result.
3. ```demo.avi```: Simulation video result.
