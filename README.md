# PyTorch Beginner Workshop

## Introduction

These are the updated versions of notebooks used in the [PyTorch Beginner Series](https://www.youtube.com/playlist?list=PL_lsbAsL_o2CTlGHgMxNrKhzP97BaG9ZN) YouTube playlist, created by [Brad Heintz](https://github.com/fbbradheintz).

## Outline

| | Title | Video | Notebook |
| --- | --- | --- | --- |
| 1 | Introduction to PyTorch | [+](https://www.youtube.com/watch?v=IC0_FRiX-sw&list=PL_lsbAsL_o2CTlGHgMxNrKhzP97BaG9ZN&index=1&pp=iAQB) | [+](./1_Overview/) |
| 2 | Introduction to PyTorch Tensors | [+](https://www.youtube.com/watch?v=r7QDUPb2dCM&list=PL_lsbAsL_o2CTlGHgMxNrKhzP97BaG9ZN&index=2&pp=iAQB) | [+](./2_Introduction_to_Tensors/2_Introduction_to_Tensors.ipynb) |
| 3 | The Fundamentals of Autograd | [+](https://www.youtube.com/watch?v=M0fX15_-xrY&list=PL_lsbAsL_o2CTlGHgMxNrKhzP97BaG9ZN&index=3&pp=iAQB) | [+](./3_The_Fundamentals_of_Autograd/3_The_Fundamentals_of_Autograd.ipynb) |
| 4 | Building Models with PyTorch | [+](https://www.youtube.com/watch?v=OSqIP-mOWOI&list=PL_lsbAsL_o2CTlGHgMxNrKhzP97BaG9ZN&index=4&pp=iAQB) | [+](./4_Building_Models_in_PyTorch/4_Building_Models_in_PyTorch.ipynb) |
| 5 | PyTorch TensorBoard Support | [+](https://www.youtube.com/watch?v=6CEld3hZgqc&list=PL_lsbAsL_o2CTlGHgMxNrKhzP97BaG9ZN&index=5&pp=iAQB) | [+](./5_TensorBoard_Support_in_PyTorch/5_TensorBoard_Support_in_PyTorch.ipynb) |
| 6 | Training with PyTorch | [+](https://www.youtube.com/watch?v=jF43_wj_DCQ&list=PL_lsbAsL_o2CTlGHgMxNrKhzP97BaG9ZN&index=6&pp=iAQB) | [+](./6_Model_Training_with_PyTorch/6_Model_Training_with_PyTorch.ipynb) |
| 7 | Model Understanding with Captum | [+](https://www.youtube.com/watch?v=Am2EF9CLu-g&list=PL_lsbAsL_o2CTlGHgMxNrKhzP97BaG9ZN&index=7&pp=iAQB) | [+](./7_Model_Understanding_with_Captum/7_Model_Understanding_with_Captum.ipynb) |
| 8 | Production Inference Deployment with PyTorch | [+](https://www.youtube.com/watch?v=Dk88zv1KYMI&list=PL_lsbAsL_o2CTlGHgMxNrKhzP97BaG9ZN&index=8&pp=iAQB) | [+](./8_Production_Inference_Deployment_with_PyTorch/) |

## Installation

Follow one of the methods below to set up everything and install all necessary dependencies.

### Method 1: Manual Way

#### Installing Miniconda

1. Install `miniconda` (or `anaconda`).

```bash
mkdir -p ~/miniconda3
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O ~/miniconda3/miniconda.sh
bash ~/miniconda3/miniconda.sh -b -u -p ~/miniconda3
rm -rf ~/miniconda3/miniconda.sh

~/miniconda3/bin/conda init bash
conda config --set auto_activate_base false
```

2. Change the solver to speed up the process of installing new packages.

```bash
conda update -n base conda
conda install -n base conda-libmamba-solver
conda config --set solver libmamba

conda config --add channels conda-forge
```

#### Setting up the Environment

3. Create a new `conda` environment.

```bash
conda create -n ai -y
```

4. Install essential packages.

```bash
conda install -c conda-forge -n ai jupyterlab numpy matplotlib -y
conda install -c pytorch -c nvidia -n ai pytorch torchvision torchaudio pytorch-cuda=12.1 -y
```

Replace `12.1` with your `cuda` version extracted from the `nvidia-smi` output.

5. Install `TensorBoard`.

```bash
conda install -c conda-forge -n ai tensorboard -y
```

If you encounter any problems due to incompatibility with the latest NumPy version, run the following commands instead:

```bash
conda activate ai
pip3 install tb-nightly
```

6. Install `captum`.

```bash
conda install -c pytorch -n ai captum -y
pip install --upgrade --quiet jupyter_client ipywidgets
conda install -c conda-forge -n ai flask flask-compress
```

7. Export installed packages for further use.

```bash
conda activate ai
conda env export > environment.yml
pip3 freeze > requirements.txt
```

### Method 2: Automatic Way

```bash
conda env create -f environment.yml
conda activate ai
pip3 install -r requirements.txt
```