# NABERT-Large+
[**Getting Started**](#getting-started) | [**Results**](#results)



This repository provides:
* Reproduction guides and results(training curves) of:
    * NAQANET
    * NABERT+
    * NAQANet
* We also retrained NABERT+ with BERT-Large, which gained an 10% improvement on dev datasets of [Discrete Reasoning Over the content of Paragraphs](https://allenai.org/data/drop) (DROP).
* A detailed report
* Also some failed attempts of migrating BERT encoders to RoBERTa and AlBERT (due to time limit).

The codes and training configs are based on [@raylin1000](https://github.com/raylin1000) and AI2.



It is also a project for MSRA-USTC Joint PhD Innovation Project 2022.

<a href="https://pytorch.org/get-started/locally/"><img alt="PyTorch" src="https://img.shields.io/badge/PyTorch-ee4c2c?logo=pytorch&logoColor=white"></a>
<a href="https://github.com/allenai/allennlp"><img alt="Config: AllenNLP" src="https://img.shields.io/badge/Config-AllenNLP-89b8cd"></a>



## Getting Started

Install dependencies

```bash
# clone project
git clone https://github.com/BC-Li/nabert-large
cd nabert-large

# [OPTIONAL] create conda environment
conda create -n myenv python=3.7
conda activate myenv

# install pytorch according to instructions
# https://pytorch.org/get-started/

# install requirements
pip install -r requirements.txt
```

Running NAQANet Baseline:

```bash
allennlp train /nabert-large/src/baseline/config/naqanet.jsonnet -s /nabert-large/src/baseline/storage --include-package baseline
```

Train starfall with config from [src/starfall/config](configs/experiment/)

```bash
allennlp train /nabert-large/src/nabert-large/config/starfall.jsonnet -s /nabert-large/src/nabert-large/storage --include-package nabert-large
```

TensorBoard:

```bash
tensorboard --logdir="/nabert-large/src/nabert-large/storage"
```

## Results

### NAQANet Baseline:

| Train Batch EM                                      | Train Batch F1                              | Train EM                        | Train F1                        |
| --------------------------------------------------- | ------------------------------------------- | ------------------------------- | ------------------------------- |
| ![train_batch_em (1)](/imgs/naqanet/train_batch_em.svg) | ![train_batch_f1](/imgs/naqanet/train_batch_f1.svg) | ![train_em](/imgs/naqanet/train_em.svg) | ![train_f1](/imgs/naqanet/train_f1.svg) |

| Train Loss                          | Validation EM                             | Validation F1                             |
| ----------------------------------- | ----------------------------------------- | ----------------------------------------- |
| ![train_loss](/imgs/naqanet/train_loss.svg) | ![validation_em](/imgs/naqanet/validation_em.svg) | ![validation_f1](/imgs/naqanet/validation_f1.svg) |

### NABERT:

| Train Batch EM                                         | Train Batch F1                                         | Validation/Train EM              | Validation/Train F1              |
| ------------------------------------------------------ | ------------------------------------------------------ | -------------------------- | -------------------------- |
| ![epoch_metrics_em](/imgs/nabert/epoch_metrics_em.svg) | ![epoch_metrics_f1](/imgs/nabert/epoch_metrics_f1.svg) | ![em](/imgs/nabert/em.svg) | ![f1](/imgs/nabert/f1.svg) |


### NABERT+

| Train Batch EM                                               | Train Batch F1                                               | Validation/Train EM                                                | Validation/Train F1                                                |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| ![epoch_metrics_em](/imgs/nabert+/epoch_metrics_em.svg) | ![epoch_metrics_f1](/imgs/nabert+/epoch_metrics_f1.svg) | ![em](/imgs/nabert+/em.svg) | ![f1](/imgs/nabert+/f1.svg) |

