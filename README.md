# Code for Semi-supervised Formality Style Transfer

This is the code for the paper "Semi-supervised Formality Style Transfer using Language ModelDiscriminator and Mutual Information Maximization" (EMNLP 2020 Findings).

## Installation

The code is based on Fairseq (https://github.com/pytorch/fairseq). Please install Pytorch (>=1.2) with CUDA support, and then run

    pip install --editable setup.py
Further instructions can be found on Fairseq official page.

## Dataset and Pre-Processing

The Grammarly Yahoo Corpus Dataset (GYAFC) is available on request from [here](https://github.com/raosudha89/GYAFC-corpus). Please download it and place it in the root directory. 

To preprocess the dataset, run

    bash preprocess.sh [options]
We followed the same instructions as [Fairseq's BART model](https://github.com/pytorch/fairseq/blob/master/examples/bart/README.summarization.md). Follow the instructions for further converting the data to binary format that can be used for training.

## Training

Download the pre-trained "bart.large" model. To start training, run 

    bash pipeline.sh [options]

The details of all parameters are given in [fairseq/options.py](fairseq/options.py). For details on parameters and values, refer to the paper and appendix.

## Evaluation and Outputs

For generation, run 

    python evaluation/gen.py

Some folder paths may need to be changed depending on configuration. For evaluation and BLEU scores, run

    python evaluation/calc_score.py path_to_output_file

The outputs for our and various other models are given in [evaluation/outputs](evaluation/outputs). As mentioned in Table 4 of the paper, we provide outputs for Hybrid Annotations, Pretrained w/ rules, Ours and Target. "\_family" refers to F&R Domain and "\_music" refers to E&M Domain.
