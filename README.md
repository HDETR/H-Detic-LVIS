# H-Detic-LVIS

This is the official implementation of the paper "[DETRs with Hybrid Matching](https://arxiv.org/abs/2207.13080)". 

Authors: Ding Jia, Yuhui Yuan, Haodi He, Xiaopei Wu, Haojun Yu, Weihong Lin, Lei Sun, Chao Zhang, Han Hu

## Model ZOO

We provide a set of baseline results and trained models available for download:

### Models with the ResNet-50 backbone
<table><tbody>
<!-- START TABLE -->
<!-- TABLE HEADER -->
<th valign="bottom">Name</th>
<th valign="bottom">Backbone</th>
<th valign="bottom">query</th>
<th valign="bottom">epochs</th>
<th valign="bottom">AP</th>
<th valign="bottom">download</th>
<!-- TABLE BODY -->
 <tr><td align="left"><a href="configs/BoxSup-DeformDETR_L_R50_2x.yaml">Deformable-DETR + tricks</a></td>
<td align="center">R50</td>
<td align="center">300</td>
<td align="center">24</td>
<td align="center">32.2</td>
<td align="center"><a href="https://github.com/HDETR/H-Detic-LVIS/releases/download/v0.1/DeformableDetr_R50.pth">model</a></td>
 <tr><td align="left"><a href="configs/BoxSup-DeformDETR_L_SwinB_4x.yaml">Deformable-DETR + tricks</a></td>
<td align="center">SwinB</td>
<td align="center">300</td>
<td align="center">48</td>
<td align="center">44.6</td>
<td align="center"><a href="https://github.com/HDETR/H-Detic-LVIS/releases/download/v0.1/DeformableDetr_SwinB.pth">model</a></td>
</tr>
</tr>
 <tr><td align="left"><a href="configs/BoxSup-DeformDETR_L_SwinL_4x.yaml">Deformable-DETR + tricks</a></td>
<td align="center">SwinL</td>
<td align="center">300</td>
<td align="center">48</td>
<td align="center">47.0</td>
<td align="center"><a href="https://github.com/HDETR/H-Detic-LVIS/releases/download/v0.1/DeformableDetr_SwinL.pth">model</a></td>
</tr>
</tr>
 <tr><td align="left"><a href="configs/BoxSup-H-DeformDETR_L_R50_2x_t900_group5.yaml">H-Deformable-DETR + tricks</a></td>
<td align="center">R50</td>
<td align="center">300</td>
<td align="center">24</td>
<td align="center">33.5</td>
<td align="center"><a href="https://github.com/HDETR/H-Detic-LVIS/releases/download/v0.1/H-DeformableDetr_R50.pth">model</a></td>
</tr>
</tr>
 <tr><td align="left"><a href="configs/BoxSup-H-DeformDETR_L_SwinB_4x_t900_group5.yaml">H-Deformable-DETR + tricks</a></td>
<td align="center">SwinB</td>
<td align="center">300</td>
<td align="center">48</td>
<td align="center">46.0</td>
<td align="center"><a href="https://github.com/HDETR/H-Detic-LVIS/releases/download/v0.1/H-DeformableDetr_SwinB.pth">model</a></td>
</tr>
</tr>
 <tr><td align="left"><a href="configs/BoxSup-H-DeformDETR_L_SwinL_4x_t900_group5.yaml">H-Deformable-DETR + tricks</a></td>
<td align="center">SwinL</td>
<td align="center">300</td>
<td align="center">48</td>
<td align="center">47.9</td>
<td align="center"><a href="https://github.com/HDETR/H-Detic-LVIS/releases/download/v0.1/H-DeformableDetr_SwinL.pth">model</a></td>
</tr>
</tbody></table>

## Installation
See [install instructions](./docs/INSTALL.md).

## Data
See [prepare datasets](./datasets/README.md).

## Run
### To train a model using 8 cards

```Bash
DETECTRON2_DATASETS=<datasets_path> python train_net.py --num-gpus 8 --resume --config-file <config_file> --eval-only
```

To train/eval a model with the swin transformer backbone, you need to download the backbone from the [offical repo](https://github.com/microsoft/Swin-Transformer#main-results-on-imagenet-with-pretrained-models) frist and specify argument`--pretrained_backbone_path` like [our configs](./configs/two_stage/deformable-detr-hybrid-branch/36eps/swin).

### To eval a model using 8 cards

```Bash
DETECTRON2_DATASETS=<datasets_path> python train_net.py --num-gpus 8 --resume --config-file <config_file> --eval-only MODEL.WEIGHTS /path/to/weight.pth
```

## Modified files 

We modified `detic/modeling/meta_arch/d2_deformable_detr.py` to support one-to-many matching loss.

Other modifications are under `third_party/Deformable-DETR`, for more information, please see [here](https://github.com/HDETR/H-Deformable-DETR#modified-files-compared-to-vanilla-deformable-detr).


## Citing H-Detic-LVIS
If you find H-Detic-LVIS useful in your research, please consider citing:

```bibtex
@article{jia2022detrs,
  title={DETRs with Hybrid Matching},
  author={Jia, Ding and Yuan, Yuhui and He, Haodi and Wu, Xiaopei and Yu, Haojun and Lin, Weihong and Sun, Lei and Zhang, Chao and Hu, Han},
  journal={arXiv preprint arXiv:2207.13080},
  year={2022}
}

@inproceedings{zhou2021detecting,
  title={Detecting Twenty-thousand Classes using Image-level Supervision},
  author={Zhou, Xingyi and Girdhar, Rohit and Joulin, Armand and Kr{\"a}henb{\"u}hl, Philipp and Misra, Ishan},
  booktitle={arXiv preprint arXiv:2201.02605},
  year={2021}
}
```

## Acknowledgement 

This repo is modified based on [Detic](https://github.com/facebookresearch/Detic).
