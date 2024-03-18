Okay, got it. I've updated the README to include the information about the GLUE datasets version:

# GitHub Repository: Task-Specific Finetuning of Large Language Models

This GitHub repository contains a suite of Jupyter notebooks that explore different techniques for fine-tuning large language models (LLMs) on various natural language processing (NLP) tasks.

## Table of Contents
1. [Introduction](#introduction)
2. [Repository Structure](#repository-structure)
3. [Datasets](#datasets)
4. [Techniques](#techniques)
   1. [Prefix Tuning](#prefix-tuning)
   2. [Full Fine-tuning](#full-fine-tuning)
   3. [LoRA](#lora)
   4. [Single Layer on Top of LLM](#single-layer-on-top-of-llm)
5. [Differential Privacy](#differential-privacy)
6. [Hyperparameters](#hyperparameters)


## Introduction
This repository is designed to provide a comprehensive exploration of different fine-tuning techniques for LLMs on various NLP tasks. The goal is to compare the performance and characteristics of these techniques, as well as the impact of applying differential privacy to the training process.

## Repository Structure
The repository contains the following Jupyter notebooks:

1. `datasets.ipynb`: This notebook downloads the GLUE datasets (SST-2, QNLI, MNLI, QQP), preprocesses them using a BERT tokenizer, and saves the tokenized datasets to disk.
2. `prefixes_prompts.ipynb`: This notebook demonstrates the Prefix Tuning (P-tuning V2) technique for fine-tuning the LLM on the tasks.
3. `full_finetuning.ipynb`: This notebook shows the standard full fine-tuning approach for the LLM on the tasks.
4. `lora.ipynb`: This notebook explores the LoRA (Low-Rank Adaptation) technique for fine-tuning the LLM on the tasks.
5. `single_layer.ipynb`: This notebook demonstrates fine-tuning the LLM by adding a single layer on top of the model for the tasks.

## Datasets
The repository uses the GLUE datasets version 2.15 due to issues with numpy in the latest version. The datasets used are:

- **SST-2**: Stanford Sentiment Treebank, a binary sentiment classification task.
- **QNLI**: Question-Answering NLI, a natural language inference task.
- **MNLI**: Multi-Genre Natural Language Inference, a natural language inference task.
- **QQP**: Quora Question Pairs, a paraphrase detection task.

These datasets are automatically downloaded and preprocessed in the `datasets.ipynb` notebook.
## Differential Privacy
The training loops in all the notebooks apply differential privacy using the Opacus library to ensure the privacy of the training data.
- Grad has been set to 0.7
- Epsilon has been set to 3 and infinity(no privacy)
- Delta has been set to inverse of length of training set for every dataset. 

## Hyperparameters
The hyperparameters used in the fine-tuning process are more or less the same across all the tasks and techniques.
- Epochs = 20,25,30
- Batch Size = 1024
- Learning rate ranges from 0.001 to 0.05
