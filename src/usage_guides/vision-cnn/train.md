# Train

> `cnn train`

Use `cnn train -h` to view concise subcommand usage information.

The train subcommand uses the `./output/` directory to save training artefacts
and exported model weights. This directory is relative to your current working
directory (check with `pwd`). Each model will get its own folder in this
directory, so the folder structure will likely look something like this:

```
output/
 ├── my_first_model/
 │    └── ...
 ├── model_improved/
 │    └── ...
 ├── model_improved_with_higher_learning_rate/
 │    └── ...
 └── ...
```

The models folder name is the only required argument when executing each of the
training subcommands (`new` or `resume`). Attempting to use a name that already
exists will fail, unless you use `--force` or `-f`.

Both training a new model and resuming/fine-tuning an existing model share a
number of common arguments; the full table can be found [here](arguments.md).

## Training A New Model

> `cnn train new`

Use `cnn train new -h` to view concise subcommand usage information.

This subcommand has a single required argument, which will be the name of the
folder under `./outputs/` that the artefacts and model weights are placed into.
E.g. `cnn train new model_1` will output into the folder at
`./outputs/model_1/`.

After executing the command, a textual user interface will appear which displays
training progress and metrics. **The first time you run the command, it may take
a while before the training actually begins, this is the the program
automatically tuning itself to your hardware**.

Once the training has completed, a summary of the model struture and training
metrics will be printed to the terminal. If you included the `--evaluate`
argument (highly recommended), the program with automatically run the evaluation
procedure, printing a summary of the result to the terminal and saving more
detailed information to `./reports/`.

## Resuming/Fine-tuning An Existing Model

> `cnn train resume`

Use `cnn train resume -h` to view concise subcommand usage information.

This subcommand has a single required argument, which will be the name of the
folder under `./outputs/` that the model is loaded and resumed from.

By default, the `resume` subcommand will output directly back into the model
folder that it loaded from. This can be changed by using
`--output <new_model_folder>` or just `-o <new_model_folder>`. E.g.
`cnn train resume model_1 -o model_1-prime`.
