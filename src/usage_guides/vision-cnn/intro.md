# Vision-CNN Introduction

The [vision-cnn](https://github.com/laser-vision-system/vision-cnn) repository
holds the code for training and running evaluation inference on a Convolutional
Neural Network.

This repository uses the
[dataset-loader](https://github.com/laser-vision-system/dataset-loader)
repository as a submodule, as well as the datasets hosted on HuggingFace.

The primary method of interacting with this code library is through the included
command-line interface (CLI). You can...

- [Train a new model from scratch:](train_new.md) `vision-cnn train new`

- [Resume training (finetune) on an existing model:](train_resume.md) `vision-cnn train resume`

- [Run inference on a model:](infer.md) `vision-cnn infer`

You can use `vision-cnn help <subcommand>` to see more information.
