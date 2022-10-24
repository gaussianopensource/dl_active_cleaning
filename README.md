# A Deep-Learning-based System for Indoor Active Cleaning (IROS 2022)
### [Project Page](https://gaussianopensource.github.io/projects/active_cleaning/) | [Paper](https://gaussianopensource.github.io/projects/active_cleaning/files/IROS_2022_GS.pdf) | [Dataset](https://drive.google.com/file/d/1HBkpmn9f-fprTxk8R75j7WS4eDw1mnlp/view?usp=sharing)
Dataset and evaluation code our IROS 2022 paper.<br>

A Deep-Learning-based System for Indoor Active Cleaning](https://gaussianopensource.github.io/projects/active_cleaning/) <br>

[Yike Yun](https://scholar.google.com.sg/citations?user=gCQdrmUAAAAJ&hl=zh-CN)\*<sup>1</sup>, Linejie Hou, [Zijian Feng](https://vincentfung13.github.io/)\*<sup>1</sup>, Wei Jin, Yang Liu, Heng Wang,  Ruonan He, Weitao Guo, Bo Han, [Baoxing Qin](https://scholar.google.com.sg/citations?user=07p-bmYAAAAJ&hl=en), [Jiaxin Li](https://www.jiaxinli.me/)<br>
 <sup>1</sup>Gaussian Robotics  
  \*denotes equal contribution

We propose an active-cleaning framework by utilizing deep-learning methods for both solid wastes detection and liquid stains segmentation. Our system consists of 4 components: a Perception module integrated with deep-learning models, a Post-processing module for projection, a Tracking module for map localization, and a Planning and Control module for cleaning strategies. Compared with classic approaches, our vision-based system significantly improves cleaning efficiency. Besides, we released the largest real-world indoor hybrid dirt cleaning dataset (HD10K) containing 10K labeled images, together with a track-level evaluation metric for better cleaning performance measurement. The proposed deep-learning based system is verified with extensive experiments on our dataset, and deployed to Gaussian Robotics's robots operating globally.

<img src='assets/imgs/overview.png'/>

## HD10K Dataset

### Dataset Overview

HD10K is the largest indoor real-life dirt dataset to date for cleaning robotics. Common dirt in shopping malls such as flyers/ tickets, and coffee/tea stains are targeted as solid wastes and liquid stains correspondingly. To ensure the variety of our data, we collected our dataset in 3 different Chinese cities. We use our robot's front RGB camera to record the data, during collection, dirt are randomly placed on the floor mimicking the real-life scenes and the robot was manually pushed using random routines. The collected data are in the form of video sequences in 10FPS; key-frames are extracted for annotation by thresholding frame similarity at 2Hz. Bounding boxes and segmentation masks are applied accordingly for solid wastes and liquid stains. Only key-frames are labeled for training data while the entire sequence is labeled for testing data.

<img src='assets/imgs/dataset_sample.png'/>

### Dataset Structure

The HD10K dataset can be downloaded from [Google Drive](https://drive.google.com/file/d/1HBkpmn9f-fprTxk8R75j7WS4eDw1mnlp/view?usp=sharing). The dataset has the following structure:

```
├── test
│   ├── images
│   │   ├── scene_1
│   │   └── scene_2
│   ├── liquid_dirts_masks
│   │   ├── scene_1
│   │   └── scene_2
│   ├── solid_dirts_bboxes
│   │   ├── scene_1
│   │   └── scene_2
│   └── tfs
│       ├── scene_1
│       └── scene_2
└── train
    ├── liquid_dirts
    │   ├── images
    │   │   ├── scene_0
    │   │   └── scene_1
    │   └── liquid_dirts_masks
    │       ├── scene_0
    │       └── scene_1
    └── solid_dirts
        ├── images
        │   ├── scene_0
        │   └── scene_1
        └── solid_dirts_bboxes
            ├── scene_0
            └── scene_1
```

As stated in the paper, the dataset is split into a training set and a test set. In the test set, in addition to the solid dirts bounding boxes and the liquid dirts masks annotation, we provide the camera parameters for each frame in the test set, which includes a homography matrix that transfers image coordinates to BEV coordinates, and the extrinsics of each frame.

### Bounding Box Format

Our bounding box annotations follow the COCO format, where each image has a text file with the same basename. In each text file, a bounding box is represented as one line with the following format:

```
# Cls cx cy w h
0 0.284078 0.103906 0.029188 0.010229
```

### Segmentation Mask format

For each image, we provide a PNG file that stores pixel-level mask annotation, where in RGB format, [0, 0, 0] indicates background and [255, 0, 0] indicates liquid dirts.

## Citation 

If you find our work helpful to your research, please cite our paper:
```
@inproceedings{dl_active_cleaning_iros,
  title={A Deep-Learning-based System for Indoor Active Cleaning},
  author={Yike Yun and Linjie Hou and Zijian Feng and Wei Jin and Yang Liu and Heng Wang and Ruonan He and Weitao Guo and Bo Han and Baoxing Qin and Jiaxin Li},
  year={2022},
  booktitle={IEEE/RSJ International Conference on Robots and Systems},
}
```