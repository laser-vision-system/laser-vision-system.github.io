# Vision-CNN Introduction

The [vision-cnn](https://github.com/laser-vision-system/vision-cnn) repository
holds the code for training and running evaluation inference on a Convolutional
Neural Network.

This repository uses the
[dataset-loader](https://github.com/laser-vision-system/dataset-loader)
repository as a submodule, as well as the datasets hosted on HuggingFace.

The primary method of interacting with this code library is through the included
command-line interface (CLI). You can...

- [Train a new model from scratch:](train.md#training-a-new-model)
  `cnn train new`

- [Resume training (finetune) on an existing model:](train.md#resumingfine-tuning-an-existing-model)
  `cnn train resume`

- [Run inference on a model:](infer.md) `cnn infer`

You can use `cnn help` to see basic command information, `cnn help <subcommand>`
to see detaiked information, and `cnn <subcommand> -h` for concise usage
information.
