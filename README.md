# DeepLab - Pytorch 
## Kevin Wang - COMS4998: A Deep Learning Project

Repo is based on https://github.com/VainF/DeepLabV3Plus-Pytorch

### 1. Install Requirements

```bash
pip install -r requirements.txt
```

### 2. Train the model on Cityscapes

#### 2.1 Download and Extract Dataset

Download the [CityScapes Dataset](https://www.cityscapes-dataset.com/). You will need a free account 
to do so. Download "gtFine" and "leftImg8bit" datasets.

Extract two zip files ```gtFine_trainvaltest.zip```, ```leftImg8bit_trainvaltest.zip``` and 
extract it to the following folder structure:

```
/datasets
    /data
        /cityscapes
            /gtFine
            /leftImg8bit
```


#### 2.2 Start Visdom Server (Visualize Training)

```bash
# First start visdom server on port 28333
visdom -port 28333
````

#### 2.1 Run Training Command on Cityscapes Dataset

```bash
py main.py --model deeplabv3plus_mobilenet --dataset cityscapes --enable_vis --vis_port 28333 --gpu_id 0  --lr 0.1  --crop_size 768 --batch_size 2 --output_stride 16 --data_root ./datasets/data/cityscapes 
```

### 3. Make your Prediction
Our examples are in ```test_images``` and results are stored in ```test_results```

Single image:
```bash
py predict.py --input /test_images/1325466082.jpg  --dataset cityscapes --model deeplabv3plus_mobilenet --ckpt checkpoints/best_deeplabv3plus_mobilenet_cityscapes_os16.pth --save_val_results_to test_results
```

Image folder:
```bash
py predict.py --input /test_images --dataset cityscapes --model deeplabv3plus_mobilenet --ckpt checkpoints/best_deeplabv3plus_mobilenet_cityscapes_os16.pth --save_val_results_to test_results
```


