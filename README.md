# NCVPRIPG 2023 Challenge on Writer Verification

![](https://vl2g.github.io/challenges/wv2023/images/intro_figure.png)

**Challenge Webpage**: [Summer Challenge on Writer Verification, under NCVPRIPG'23](https://vl2g.github.io/challenges/wv2023)  

**Kaggle Link**: [Summer Challenge on Writer Verification](https://www.kaggle.com/competitions/summer-challenge-on-writer-verification23-finale/leaderboard)  

**Wandb logs**: [wandb](https://wandb.ai/manan-shah/NCVPRIPG23%20Writer%20Verification?workspace=user-manan-shah)

**Team Name**: MaSha

## Environment

```shell
conda env create -f environment.yml
conda activate ncvp
mkdir -p data/raw
```

Download and extract the dataset including the val and test CSVs in `data/raw`.

## Download Checkpoints
The checkpoint for the best trained model can be found at [Google Drive](https://drive.google.com/file/d/1848Iu-JKXWSBgFvBN50-l-ZXXKgqkRJf/view?usp=sharing). You can download this and store it at a desired location. For downloading, you can use [gdown](https://github.com/wkentaro/gdown).

```shell
mkdir pretrained
cd pretrained
gdown 'https://drive.google.com/uc?id=1848Iu-JKXWSBgFvBN50-l-ZXXKgqkRJf'
```

## Generating Results on Test Set

```shell
python inference.py --ckpt pretrained/model_best_base.pth.tar
```

## Training

All runs have been logged using [wandb](https://wandb.ai/manan-shah/NCVPRIPG23%20Writer%20Verification?workspace=user-manan-shah)

To start training, run
```shell
python train.py
```
You might have to change the inputs to `wandb.init()` function.

To reproduce the best results, pass the best config
```shell
python train.py --config cfgs/best.yml
```

To disable wandb while training, run
```shell
WANDB_MODE=disabled python train.py
```