# DeepLab - Pytorch - Kevin Wang

Repo is based on https://github.com/VainF/DeepLabV3Plus-Pytorch

### 1. Install Requirements

```bash
pip install -r requirements.txt
```

### 2. Train the model on Cityscapes

#### 2.1 Start Visdom Server (Visualize Training)

```bash
# First start visdom server on port 28333
visdom -port 28333
````

#### 2.2 Run Training Command on Cityscapes Dataset

```bash
py main.py --model deeplabv3plus_mobilenet --dataset cityscapes --enable_vis --vis_port 28333 --gpu_id 0  --lr 0.1  --crop_size 768 --batch_size 2 --output_stride 16 --data_root ./datasets/data/cityscapes 
```

### 3. Make your Prediction (examples are in cityscape dataset folders)
Single image:
```bash
py predict.py --input datasets/data/cityscapes/leftImg8bit/train/bremen/bremen_000000_000019_leftImg8bit.png  --dataset cityscapes --model deeplabv3plus_mobilenet --ckpt checkpoints/best_deeplabv3plus_mobilenet_cityscapes_os16.pth --save_val_results_to test_results
```

Image folder:
```bash
py predict.py --input datasets/data/cityscapes/leftImg8bit/train/bremen  --dataset cityscapes --model deeplabv3plus_mobilenet --ckpt checkpoints/best_deeplabv3plus_mobilenet_cityscapes_os16.pth --save_val_results_to test_results
```


