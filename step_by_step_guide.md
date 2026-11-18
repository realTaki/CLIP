# Experimental training setup

Install PyTorch and torchvision for your CPU or CUDA setup, then run these
commands from the repository root:

```bash
python -m pip install .
python -m pip install pandas transformers wandb
```

In `config.py`, set `image_path` to the image directory and `captions_path` to
a UTF-8 file with one image and caption per line, separated by a tab. The image
filename is relative to `image_path`. The script uses CUDA when available and
otherwise runs on the CPU. Adjust the batch size and worker count in
`config.py` for your machine.

```bash
mkdir -p models
WANDB_MODE=offline python main.py
```

The script creates a validation split and saves the best checkpoint under
`models/`. Omit `WANDB_MODE=offline` if you want to log runs to a configured
Weights & Biases account.
