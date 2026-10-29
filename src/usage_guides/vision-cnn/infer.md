# Running Evaluation Inference On A Model

> `cnn infer`

Use `cnn infer -h` to view concise subcommand usage information.

This subcommand has a single required argument, which will be the name of the
folder under `./outputs/` that the model is loaded to run inference on.

If the model weights file itself has a name different to `model.bpk`, you can
optionally specify it with `--name`.

You can choose which dataset to run inference on with `--dataset` or `-d`. The
options that you can choose from are listed with `cnn infer -h`.

By default, inference will only run on a single sample, you can choose a
different number with `--num-samples`.

If you wish to perform a full evaluation, you can use the `--evaluate-all`
argument. You are required to also include `--report-dir` to specify a place to
save the output of the evaluation. If the output folder already exists, you must
use `--force` or `-f` to replace it.

You can configure the evaluation with `--evaluation-batch-size` and
`--evaluation-split`.

<!-- a summary of the result to the terminal and saving more detailed information to `./reports/`.-->
