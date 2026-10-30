# Arguments

Both `cnn train new` and `cnn train resume` share a large number of arguments.
For simplicity, they are all listed here.

They are also viewable with either `cnn help train new` or
`cnn help train resume`.

| Argument                    | Description                                                                                                                                                            | Equivalent Environment Variable      |
| --------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------ |
| `--dataset`/`-d`            | Select the dataset source to use when training the model.                                                                                                              | N/A                                  |
| `--force`/`-f`              | Replace an output directory if it exists, deleting all contents.                                                                                                       | N/A                                  |
| `--name <MODEL_NAME>`       | Choose a custom name for the output model weights file. Defaults to `model`.                                                                                           | `VISION_CNN_MODEL_NAME`              |
| `--evaluate`                | Automatically run evaluation once the training completes. The result will be saved into the `./reports/` directory with a matching name.                               | N/A                                  |
| `--dry-run`                 | Don't export the model weights once completed. Training artefacts are saved to a temporary directory.                                                                  | N/A                                  |
| `--num-epochs`              | Epochs to run in this invocation. This is considered to be additional epochs when resuming.                                                                            | `VISION_CNN_NUM_EPOCHS`              |
| `--batch-size`              | The number of images in each batch. High values use substantially more video memory (VRAM).                                                                            | `VISION_CNN_BATCH_SIZE`              |
| `--num-workers`             | How many threads are allocated to loading the dataset.                                                                                                                 | `VISION_CNN_NUM_WORKERS`             |
| `--seed`                    | The seed value used for random number generation.                                                                                                                      | `VISION_CNN_SEED`                    |
| `--learning-rate`           | The initial learning rate. Higher values increase how quickly the weights approach the goal value but also increase instablility.                                      | `VISION_CNN_LEARNING_RATE`           |
| `--decay-rate`              | Scalar factor for the inverse time decay scheduler. This is how quickly the learning rate reduces over time.                                                           | `VISION_CNN_DECAY_RATE`              |
| `--decay-steps`             | The learning-rate decay interval (`0` derives it automatically). This can be used when the number of iterations per epoch has changed; due to the batch size or other. | `VISION_CNN_DECAY_STEPS`             |
| `--early-stopping-patience` | How many validation epochs without improvement before the system automatically stops.                                                                                  | `VISION_CNN_EARLY_STOPPING_PATIENCE` |
