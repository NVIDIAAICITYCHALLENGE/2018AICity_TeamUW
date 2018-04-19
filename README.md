# Single-camera and Inter-camera Vehicle Tracking and 3D Speed Estimation Based on Fusion of Visual and Semantic Features for NVIDIA AI City Challenge Workshop at CVPR 2018

This repository contains our source code of Track 1 and Track 3 in the NVIDIA AI City Challenge Workshop at CVPR 2018.

The source code of Track 1 is built in MATLAB and C++, with our trained YOLOv2 model provided. 

The source code of Track 3 is developed in Python and C++. 

Both Track 1 and Track 3 have been tested on Linux and Windows. Dependencies include CUDA, cuDNN and OpenCV library.

## Introduction

### NVIDIA AI City Challenge Workshop at CVPR 2018

The NVIDIA AI City Challenge Workshop at CVPR 2018 will specifically focus on ITS problems such as

1. Estimating traffic flow characteristics, such as speed
2. Leveraging unsupervised approaches to detect anomalies caused by crashes, stalled vehicles, etc. This is the only way to get the humans in the loop pay attention to meaningful visual information
3. Multi-camera tracking, and object re-identification in urban environments

Our team participated in 2 out of 3 tracks: 

1. Track 1 - Traffic Flow Analysis - Participating teams submit results for individual vehicle speed for a test set containing 27 1-minute videos. Performance is evaluated based on ground truth generated by a fleet of control vehicles that were driven during the recording. Evaluation for Challenge Track 1 is based on detection rate of the control vehicles and the root mean square error of the predicted control vehicle speeds.
2. Track 3 - Multi-camera Vehicle Detection and Reidentification - Participating teams identify all vehicles that are seen passing at least once at all of 4 different locations in a set of 15 videos. Evaluation for Challenge Track 3 is based on detection accuracy and localization sensitivity for a set of ground-truth vehicles that were driven through all camera locations at least once.

Detailed information of this challenge can be found [here](https://www.aicitychallenge.org/).

Our team achieves rank #1 in both Track 1 and Track 3. The demo videos can be viewed [here](http://allison.ee.washington.edu/thomas/aicity18/). 

### Single-camera Tracking (SCT)

In SCT, our loss function consists of motion, temporal and appearance attributes. Especially, a histogram-based adaptive appearance model is designed to encode long-term appearance change for enhanced robustness. The change of loss is incorporated with a bottom-up clustering strategy for the association of tracklets. Robust 2D-to-3D backprojection is achieved with EDA optimization applied to camera calibration for speed estimation. 

### Inter-camera Tracking (ICT)

The proposed appearance model together with DCNN features, license plates, detected car types and traveling time information are combined for the computation of cost function in ICT. 

## Code structure

### Track 1

Under the `./Track1/` folder, there are 6 software packages:
1. VDO2IMG_IPL: Converting each video file to a folder of frame images
2. CAM_CAL_IPL: Manual camera calibration based on minimization of reprojection error and EDA optimization
3. YOLO_IPL: Extension of the YOLOv2 object detector with our trained model for vehicle detection/classification
4. TC_tracker: Proposed tracklet-clustering-based tracking method
5. APP_MDL_IPL: Extraction of histogram-based adaptive apperance models and their comparison
6. SPD_EST_IPL: Speed estimation based on input of tracking results and camera parameters
Detailed description of each package is given in each subfolder. 

### Track 3

Under the `./Track3/` folder

## Reference

Z. Tang, G. Wang, H. Xiao, A. Zheng and J.-N. Hwang, "Single-camera and inter-camera vehicle tracking and 3D speed estimation based on fusion of visual and semantic features," in Proc. IEEE/CVF Conf. Comput. Vis. Pattern Recogn. Workshops (CVPRW), Jun. 2018. (to appear)

## Disclaimer

For any question you can contact [Zheng (Thomas) Tang](https://github.com/zhengthomastang).