RGB-IR Cross Modality Person Re-Identification
==============================================

Pytorch implementation of Domain Invariant and Attribute based Representation Learning for RGB-IR Cross Modality Person Re-Identification. Refer to the following [report](docs/DIRL-ABRL.pdf) for details about the model architecture and the results. 

## Dataset Preparation 

Download the following datasets and extract them in the datasets folder.

1.  RegDB Dataset [1]: The RegDB dataset can be downloaded from this [website](http://dm.dongguk.edu/link.html) by submitting a copyright form.
 (Named: "Dongguk Body-based Person Recognition Database (DBPerson-Recog-DB1)" on their website). 

2. SYSU-MM01 Dataset [2]: The SYSU-MM01 dataset can be downloaded from this [website](http://isee.sysu.edu.cn/project/RGBIRReID.htm).

## Training and Testing

1. To train the DIRL model on RegDB dataset, 

```
cd src/regdb_/
python train.py --arch resnetmid_domain --cuda --lambda-domain 1 --lambda-attribute 0
``` 
Similarly, we can train for SYSU dataset by running 'train.py' under 'src/sysu_' directory

2. To train the ABRL model on SYSU dataset, 

```
cd src/sysu_/
python train.py --arch resnetmid --cuda --lambda-domain 0 --lambda-attribute 10 --test-on-val
``` 
Similarly, we can train for SYSU dataset by running 'train.py' under 'src/sysu_' directory


- One can refer to the 'OptionsParser' function in [utils](src/regdb_/regDB_project_utils.py) file to explore the training options and parameters for regDB dataset. Similarly, for SYSU dataset refer to this [utils](src/sysu_/project_utils.py) file.
- After training is completed, the model will be tested on the test dataset automatically. 

##  References.
[1] D. T. Nguyen, H. G. Hong, K. W. Kim, and K. R. Park. Person recognition system based on a combination of body images from visible
light and thermal cameras. Sensors, 17(3):605, 2017.

[2] A. Wu, W.-s. Zheng, H.-X. Yu, S. Gong, and J. Lai. Rgb-infrared crossmodality person re-identification. In IEEE International Conference on Computer Vision (ICCV), pages 5380–5389, 2017.