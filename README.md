# Leader-based Multi-Scale Attention Deep Architecture for Person Re-identification
This repository contains the Pytorch implementation for the paper ["Leader-based Multi-Scale Attention Deep Architecture for Person Re-identification"](http://epubs.surrey.ac.uk/852875/1/final_version.pdf)

## Framework
<img src='https://github.com/naiq/MuDeep_v2/blob/master/fig/framework.png' width=500 height=300 alt='framework'>

## Getting Started
### Prerequisites
* Python 3.6 or 3.7
* Pytorch >= 1.1.0
* tensorboardX

### Prepare data
Please download Market-1501 dataset and organize it as follows

    MuDeep_v2
        ├── dataset
        │      └─ Market-1501 # for Market-1501 dataset
        │             ├── bounding_box_train
        │             ├── bounding_box_test
        │             ├── query
        │
        ├── train.py
 
 ### How to train
 In `config.py`, set configurations for training, including `NAME`, `GPU_ID` and `ROOT`. You can keep others as default to reproduce the result.
 ``` python
 # example
 __C.NAME = 'market'  # name your model, the model files (.pkl) will be saved according to this name
 __C.GPU_ID = 0,1  
 __C.ROOT = '/home/qxl/work/mudeep_v2/'  # path to your project folder, all models and log files will be saved in this folder
 ...
 ```
 
 In `train.py`, using the following command lines to train the model
 
 ``` python
 # example
 engine = MuDeep_v2(cfg)
 engine.train()
 ```
 Once trained, the models and log file will be saved in `ROOT/model/NAME/` and `ROOT/log/NAME/` respectively.
 
 By default, we evaluate the model every 5 epochs, the results will be written in `ROOT/model/NAME/opt.txt`

 
 ### How to evaluate
 In `train.py`, using the following command lines to evaluate the model
 
 ``` python
 # example
 engine = MuDeep_v2(cfg)
 engine.test(model_path='/home/qxl/work/mudeep_v2/model/market',   # path to your model
             out_name='market_evaluate'  # name the output TXT file
            )
 ```
 
 ## Result
 | **name** | **backbone** | **image size** | **mAP** | **Rank-1** | **Rank-5** | **Rank-10** | **url** |
 | :------: | :------: | :------: | :------: | :------: | :------: | :------: | :------: |
 | market_v1 | ResNet-50 | 384 x 192 | 86.87 | 95.43 | 98.46 | 99.23 | [download](https://drive.google.com/file/d/1i_avJ0_Y2hsEfqhhL4DXBrRr1NEzpwZ_/view?usp=sharing) |
 | market_v2 | ResNet-50 | 384 x 128 | 86.79 | 95.34 | 98.40 | 99.11 | [download](https://drive.google.com/file/d/1r2lsdRGFYajxtNJ7QPyqdif3DrEiHsa4/view?usp=sharing) |
 
 
 
 ## Citation
If you find this project useful in your research, please consider cite:

    @article{qian2019leader,
      title={Leader-based multi-scale attention deep architecture for person re-identification},
      author={Qian, Xuelin and Fu, Yanwei and Xiang, Tao and Jiang, Yu-Gang and Xue, Xiangyang},
      journal={IEEE transactions on pattern analysis and machine intelligence},
      volume={42},
      number={2},
      pages={371--385},
      year={2019},
      publisher={IEEE}
    }

## Contact

Any questions or discussion are welcome!

Xuelin Qian (<xlqian15@fudan.edu.cn>)
