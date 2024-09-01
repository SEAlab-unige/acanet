# Affordance segmentation of hand-occluded containers from exocentric images

[[arXiv](https://arxiv.org/abs/2308.11233v1)] 
[[webpage](https://apicis.github.io/projects/acanet.html)]
[[trained model](https://doi.org/10.5281/zenodo.8364196)]
[[mixed-reality data](https://doi.org/10.5281/zenodo.5085800)]
[[real testing data](https://doi.org/10.5281/zenodo.10708553)]
 
## Table of Contents

1. [Installation](#installation)
    1. [Setup specifics](#setup_specifics)  
    2. [Requirements](#requirements)
    3. [Instructions](#instructions)
2. [Running demo](#demo)
3. [Training and testing data](#data)   
4. [Enquiries, Question and Comments](#enquiries-question-and-comments)
5. [License](#license)

## Installation <a name="installation"></a>

### Setup specifics <a name="setup_specifics"></a>
The models testing were performed using the following setup:
* *OS:* Ubuntu 20.04.6 LTS
* *Kernel version:* 5.15.0-69-generic
* *CPU:* Intel® Core™ i9-9900 CPU @ 3.10GHz
* *Cores:* 16 
* *RAM:* 32 GB
* *GPU:* NVIDIA GeForce RTX 2080 Ti
* *Driver version:* 470.199.02
* *CUDA version:* 11.4


### Requirements <a name="requirements"></a> 
* Python 3.8
* PyTorch 1.8.0
* Torchvision 0.9.0
* OpenCV 4.8.0.76
* Numpy 1.22.1
* Tqdm 4.66.1

### Instructions <a name="instructions"></a>
```
# Create and activate conda environment
conda create -n occluded_affordance_segmentation python=3.8
conda activate occluded_affordance_segmentation
    
# Install libraries
pip install torch==1.8.0+cu111 torchvision==0.9.0+cu111 -f https://download.pytorch.org/whl/torch_stable.html
pip install onnx-tool==0.5.4 opencv-python numpy==1.22.1 tqdm
```

## Running demo <a name="demo"></a>

Download model checkpoint [ACANet.zip](https://doi.org/10.5281/zenodo.8364196), and unzip it.

Use the images in the folder *test_dir* or try with your own images. The folder structure is *DATA_DIR/rgb*. 

To run the model and visualise the output:

```
python3 demo.py --model_name=MODEL_NAME --data_dir=DATA_DIR  --checkpoint_path=CHECKPOINT_PATH --visualise_overlay=True --dest_dir=DEST_DIR
```

* Replace *MODEL_NAME* with *acanet*
* *DATA_DIR*: directory where data are stored
* *CHECKPOINT_PATH*: path to the .pth file
* *DEST_DIR*: path to the destination directory. This flag is considered only if you save the predictions ```--save_res=True``` or the overlay visualisation ```--save_overlay=True```. Results are automatically saved in *DEST_DIR/pred*, overlays in *DEST_DIR/vis*.

You can test if the model has the same performance by running inference on the images provided in *test_dir/rgb* and checking if the output is the same of *test_dir/pred* .

## Training and testing data <a name="data"></a>
To recreate the training and testing splits of the mixed-reality dataset:
1. Download the [dataset](https://doi.org/10.5281/zenodo.5085800) folders *rgb*, *mask*, *annotations*, *affordance* and unzip them in the preferred folder *SRC_DIR*.
2.  Run ```utils/split_dataset.py --src_dir=SRC_DIR --dst_dir=DST_DIR``` to split into training, validation and testing sets. *DST_DIR* is the directory where splits are saved.
3. Run ```utils/create_dataset_crops.py --data_dir=DATA_DIR --save=True --dest_dir=DEST_DIR``` to perform the cropping window procedure described in the paper. This script performs also the union between the arm mask and the affordance masks. *DATA_DIR* is the directory containing the *rgb* and *affordance* folders e.g.  *DST_DIR/training* following the naming used for the previous script. *DEST_DIR* is the destination directory, where to save cropped rgb images, and segmentation masks. 

## Enquiries, Question and Comments <a name="enquiries-question-and-comments"></a>

If you have any further enquiries, question, or comments, or you would like to file a bug report or a feature request, use the Github issue tracker. 

## License <a name="license"></a>

This work is licensed under the MIT License. To view a copy of this license, see [LICENSE](LICENSE).
