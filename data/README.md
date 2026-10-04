# CIFAR-10 Dataset Guide

This directory is designated for the **CIFAR-10** dataset used for evaluating adversarial defenses. 

## Expected Directory Structure

The code automatically downloads the dataset using `torchvision.datasets.CIFAR10`. If downloaded automatically or extracted manually, your `data/` folder must look like this:

```text
data/
└── cifar-10-batches-py/
    ├── data_batch_1
    ├── data_batch_2
    ├── data_batch_3
    ├── data_batch_4
    ├── data_batch_5
    ├── test_batch
    └── batches.meta
