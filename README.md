# Eye-Movement-Prompted Large Image Captioning Model
This repository contains the reference code for the paper [Eye-Movement-Prompted Large Image Captioning Model](https://www.sciencedirect.com/science/article/pii/S0031320324008483).

![](https://github.com/XidianYz/PR-2024-EMLIC/blob/main/framework.jpg)

## Experiment setup
please refer to [BLIP2](https://github.com/salesforce/LAVIS/tree/main/projects/blip2).

## Data preparation
* Download the Image data and annotation files of MS-COCO.
* Change the paths of Image data and annotation files in:
```bash
./lavis/configs/datasets/coco/defaults_cap.yaml
```

The proposed EMS (Based on [ScanDMM](https://github.com/xiangjieSui/ScanDMM)) generated simulated scanpaths of images according to the image features extracted by ViT-L/14. The pre-trained weights of EMS have already been saved in this project.

The pre-trained weights of other components are available [here](https://pan.baidu.com/s/1gbvZLQIVjkkhxQtxjBG3Lg). Acess code: PR24. After downloading, please modify the path of the pre-trained weights in:
```bash
./lavis/projects/blip2/eval/caption_coco_opt2.7b_eval.yaml
```

## Training
```python
python train.py  --cfg-path ./lavis/projects/blip2/train/caption_coco_ft.yaml
```
## Evaluation
```python
python evaluation.py --cfg-path ./lavis/projects/blip2/eval/caption_coco_opt2.7b_eval.yaml
```
By evaluating the pretrained model, you will get
```bash
{"Bleu_1": 0.8416596643524815, "Bleu_2": 0.7004053552456088, "Bleu_3": 0.5631765056538399, "Bleu_4": 0.44376940296846634, "METEOR": 0.31258980379624124, "ROUGE_L": 0.6190987658426934, "CIDEr": 1.4508326134641394, "SPICE": 0.24624060411514903}
```

## Acknowledgements
Thanks the outstanding baselines of [BLIP2](https://github.com/salesforce/LAVIS/tree/main/projects/blip2) and [ScanDMM](https://github.com/xiangjieSui/ScanDMM).
