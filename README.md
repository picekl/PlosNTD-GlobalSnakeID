# PlosNTD-GlobalSnakeID


# An artificial intelligence model to identify snakes from across the world: Opportunities and challenges for global health and herpetology

By Isabelle Bolon, [Lukas Picek](https://sites.google.com/view/picekl), Andrew M. Durso, Gabriel Alcoba, François Chappuis and Rafael Ruiz de Castañeda 
[MAIL](mailto:lukaspicek@gmail.com?subject=[GitHub]%20DanishFungi2020%20Project).

## Introduction



Supplementary material to [An artificial intelligence model to identify snakes from across the world: Opportunities and challenges for global health and herpetology](https://journals.plos.org/plosntds/article?id=10.1371/journal.pntd.0010647)

In order to allow full reproducibility of our results, we share the training logs, trained scripts and metadata.
- The Images, Checkpoints are not included in this GitHub repo but are available at [Lindat Repository](https://lindat.mff.cuni.cz/repository/xmlui/handle/20.500.12800/1-4773).

## Training Data

Available at -> https://lindat.mff.cuni.cz/repository/xmlui/handle/20.500.12800/1-4773.

## Training

1. Download PyTorch NGC Docker Image and RUN docker container

```
docker pull nvcr.io/nvidia/pytorch:21.07-py3
docker run --gpus all -it --rm -v local_dir:container_dir nvcr.io/nvidia/pytorch:21.07-py3
```

2. Install dependencies inside docker container

```
pip install pandas seaborn timm albumentation tqdm efficientnet_pytorch pretrainedmodels
```
3. RUN jupyterlab and start training / experiments
```
jupyter lab --ip 0.0.0.0 --port 8888 --allow-root
```
* Check your paths! 

## Results

Performance comparison for two ViT-Base/32 models trained on the SnakeCLEF2021 dataset and its “clean” subset.

|  | macro F1 [%] | Top1 Accuracy [%]|
|  | Country | Species | Genus | Species | Genus |
| ---------------- | ---- | ---- | ---- | ---- | ---- |
| Clean set        | 68.6 | 69.7 | 72.5 | 82.3 | 90.0 |
| Full set         | 75.9 | 74.2 | 77.9 | 88.2 | 93.4 |
| ---------------- | ---- | ---- | ---- | ---- | ---- |

Test time augmentations experiment for ViT-Large/16 -- 384x384.
|  | macro F1 [%] | Top1 Accuracy [%]|
|  | Country | Species | Genus | Species | Genus |
| ----------------------- | ---- | ---- | ---- | ---- | ---- |
| Baseline                | 91.1 | 88.8 | 93.2 | 94.1 | 98.4 |
| Test-time augmentation  | 91.3 | 89.1 | 92.5 | 95.7 | 98.5 |
| ----------------------- | ---- | ---- | ---- | ---- | ---- |

Achieved performance on the SnakeCLEF2021 test set using different locational data and metadata integration method. ViT-Large/16 -- 384x384.
|  | macro F1 [%] | Top1 Accuracy [%]|
|  | Country | Species | Genus | Species | Genus |
| ----------------- | ---- | ---- | ---- | ---- | ---- |
| Baseline with TTA | 91.3 | 89.1 | 92.5 | 95.7 | 98.5 |
| Country Prior     | 90.0 | 89.1 | 91.5 | 95.4 | 98.6 |
| Continents Prior  | 93.2 | 90.7 | 95.6 | 95.1 | 98.9 |
| Presence Masking  | 94.2 | 92.2 | 94.9 | 96.0 | 99.0 |
| ----------------- | ---- | ---- | ---- | ---- | ---- |


## License

The code and dataset is released under the BSD License. There is some limitations for commercial usage.
In other words, the training data, metadata, and models are available only for non-commercial research purposes only.

## Citation



```
@article{10.1371/journal.pntd.0010647,
    doi = {10.1371/journal.pntd.0010647},
    author = {Bolon, Isabelle AND Picek, Lukáš AND Durso, Andrew M. AND Alcoba, Gabriel AND Chappuis, François AND Ruiz de Castañeda, Rafael},
    journal = {PLOS Neglected Tropical Diseases},
    publisher = {Public Library of Science},
    title = {An artificial intelligence model to identify snakes from across the world: Opportunities and challenges for global health and herpetology},
    year = {2022},
    month = {08},
    volume = {16},
    url = {https://doi.org/10.1371/journal.pntd.0010647},
    pages = {1-19},
    number = {8},
}
```

## Contact

```
[Lukas Picek](lukaspicek@gmail.com, picekl@ntis.zcu.cz)
[Isabelle Bolon](Isabelle.Bolon@unige.ch)
```
