# Affordance segmentation of hand-occluded containers from exocentric images

[[arXiv](https://arxiv.org/abs/2308.11233v1)] 
[[webpage](https://apicis.github.io/projects/acanet.html)]
[[trained models](https://doi.org/10.5281/zenodo.8364196)]

# TODO:
- [x] ACANet files
- [x] Demo on images
- [ ] Other models files
- [ ] Dataset setup and scripts
- [ ] Complete missing parts of README.md
 
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
If you want to train or test your own model, you can download the mixed-reality [dataset](https://doi.org/10.5281/zenodo.5085800) used in the paper.

## Enquiries, Question and Comments <a name="enquiries-question-and-comments"></a>

If you have any further enquiries, question, or comments, or you would like to file a bug report or a feature request, use the Github issue tracker. 

## License <a name="license"></a>

This work is licensed under the MIT License. To view a copy of this license, see [LICENSE](LICENSE).
