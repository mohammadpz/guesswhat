# guesswhat

This repo aim at reproducing the results from the series of GuessWhat?! papers, namely:
- GuessWhat?! Visual object discovery through multi-modal dialogue - https://arxiv.org/abs/1611.08481
- End-to-end optimization of goal-driven and visually grounded dialogue systems - https://arxiv.org/abs/1703.05423

The code was equally developed bu Florian Strub (University of Lille) and Harm de Vries (University of Montreal)

The project is part of the CHISTERA - IGLU Project.



#### Summary:

* [Introduction](#introduction)
* [Installation](#installation)
    * [Requirements](#requirements)
    * [Submodules](#submodules)
    * [Data](#data)
* [Reproducing results](#reproducing-results)
    * [Data](#data)
    * [Train Oracle](#oracle)
    * [Train Guesser](#guesser)
    * [Train Qgen](#qgen)
* [Citation](#citation)

## Introduction

## Installation

### Requirements

The code works on both python 2 and 3. It relies on the tensorflow python API.
It requires the following python packages:

```
pip install \
    tensorflow-gpu \
    PIL \
    pikcle \
    tqdm
```

### Submodules
Our code has internal dependences. To properly clone the repo, please use the following git commands:\

```
git clone --recursive git@github.com:GuessWhatGame/guesswhat.git
```

### File architecture
In the following, we assume that the following file/folder architecture is respected:


```
guesswhat
├── config         # store the configuration file to create/train models
|   ├── oracle
|   ├── guesser
|   └── qgen
|   └── loop
|
├── out            # store the output experiments (checkpoint, logs etc.)
|   ├── oracle
|   ├── guesser
|   └── qgen
|   └── loop
|
├── data          # contains the Guesshat data
|   └── img       # contains the coco img
|
├── vqa            # vqa package dir
|   ├── datasets   # datasets classes & functions dir (vqa, coco, images, features, etc.)
|   ├── external   # submodules dir (VQA, skip-thoughts.torch)
|   ├── lib        # misc classes & func dir (engine, logger, dataloader, etc.)
|   └── models     # models classes & func dir (att, fusion, notatt, seq2vec)
|
└── src            # source files
```

Of course, one is free to change this file architecture to its need!

### Data
GuessWhat?! relies on two datasets:
 - the GuessWhat?! dataset that contains the dialogue inputs
 - The MS Coco dataset that contains the image inputs

To download the GuessWhat?! dataset please follow the following instruction:
```
wget https://s3-us-west-2.amazonaws.com/guess-what/guesswhat.train.jsonl.gz guesswhat/data/
wget https://s3-us-west-2.amazonaws.com/guess-what/guesswhat.valid.jsonl.gz guesswhat/data/
wget https://s3-us-west-2.amazonaws.com/guess-what/guesswhat.test.jsonl.gz guesswhat/data/
```

To download the MS Coco dataset, please follow the following instruction:
```
wget http://msvocds.blob.core.windows.net/coco2014/train2014.zip guesswhat/data/
unzip train2014.zip guesswhat/data/img

wget http://msvocds.blob.core.windows.net/coco2014/val2014.zip
unzip val2014.zip guesswhat/data/img
```

NB: Please check that md5sum are correct after downloading the files to check whether they have been corrupted.
To do so, you can use the following command:
```
md5sum $file
```


## Reproducing results

## Citation