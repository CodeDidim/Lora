# LoRA Dataset Maker (Local Version)

This repository contains Jupyter notebooks for creating and preparing LoRA datasets. The notebooks were originally designed for Google Colab but can be run locally on your own GPU.

## Requirements

- Python 3.10+
- A CUDA-enabled GPU with the appropriate drivers
- `aria2` and `python3.10-venv` system packages (Ubuntu example below)
- Python packages listed in `requirements.txt`
- If running on Python 3.11 or newer, make sure `timm` is version **0.9.2** or
  newer. Older releases can throw a `ValueError: mutable default <class
  'timm.models.maxxvit.MaxxVitConvCfg'> for field conv_cfg is not allowed: use
  default_factory` error when running the notebooks.

Install the system dependencies (Ubuntu/Debian example):

```bash
sudo apt-get update
sudo apt-get install -y aria2 python3.10-venv git
```

Install the Python requirements:

```bash
pip install -r requirements.txt
```

## Running the Notebook

1. Launch Jupyter:
   ```bash
   jupyter notebook
   ```
2. Open `dataset_maker.ipynb` (or `Dataset_Maker.ipynb`).
3. Ensure the variable `COLAB` at the start of the notebook is set to `False` (already the default in this version).
4. Execute the cells one by one to set up your project, download images and tag them.

The notebook will create a project directory under `./Loras` by default. Adjust paths inside the notebook if necessary. To avoid directory mismatches when calling `os.chdir`, the notebooks convert these paths to absolute form using `os.path.abspath`.

## Notes

The tagging step clones the `kohya-ss/sd-scripts` repository and installs its requirements inside a Python virtual environment. This process mirrors the behaviour of the original Colab notebook but runs entirely on your machine. On Windows, the notebook skips the `apt` command and uses `python -m venv` to create the environment automatically.

