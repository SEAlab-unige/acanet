# Affordance segmentation of hand-occluded containers from exocentric images

[[arXiv](https://arxiv.org/abs/2308.11233v1)]
[[webpage](https://apicis.github.io/projects/acanet.html)]
[[trained models](...)]
[[dataset](https://doi.org/10.5281/zenodo.5085800)]

# TODO:
- [ ] ACANet files
- [ ] Other models files
- [ ] Demo on images
- [ ] Complete missing parts of README.md
 
## Table of Contents

1. [Installation](#installation)
    1. [Setup specifics](#setup_specifics)  
    2. [Requirements](#requirements)
    3. [Instructions](#instructions)
3. [Running demo](#demo)
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


### Requirements <a name="requirements"></a>

### Instructions <a name="instructions"></a>

    # Create and activate conda environment
    conda create -n affordance_segmentation python=3.8
    conda activate affordance_segmentation
    
    # Install libraries
    pip install torch==1.8.0+cu111 torchvision==0.9.0+cu111 torchaudio==0.8.0 -f https://download.pytorch.org/whl/torch_stable.html
    pip install albumentations torchsummary segmentation-models-pytorch==0.2.1 onnx-tool==0.5.4 tensorboard opencv-python seaborn numpy==1.22.1 tqdm

## Running demo <a name="demo"></a>

To run the models and visualise the output:

    python3 test_main_<model_name>.py --data_dir=DATA_DIR --checkpoint_path=CHECKPOINT_PATH --visualise_overlay=True
* Replace *<model_name>* with one among *drnatt*, *rn18u*, *rn50f*, *acanet*
* *DATA_DIR*: directory where data are stored, with the structure `DATA_DIR/rgb`
* *CHECKPOINT_PATH*: path to the .pth file

## Enquiries, Question and Comments <a name="enquiries-question-and-comments"></a>

If you have any further enquiries, question, or comments, or you would like to file a bug report or a feature request, use the Github issue tracker. 

## License <a name="license"></a>

This work is licensed under the MIT License. To view a copy of this license, see [LICENSE](LICENSE).
