# DxMI_EasyRun

Easy-to-run version of **DxMI** for pretrained CIFAR-10 generation.

This repository is a simplified setup for running the pretrained CIFAR-10 generation pipeline from the official DxMI project without having to manually reconstruct every file and folder by yourself.

## Official Source

This project is based on the official DxMI repository:

- **Official DxMI repository**: https://github.com/swyoon/Diffusion-by-MaxEntIRL
- **Paper**: *Maximum Entropy Inverse Reinforcement Learning of Diffusion Models with Energy-Based Models* 
- **authour** : Sangwoong Yoon 
---

## What is Different in This Repository?

This repository is organized for **easy execution**.

- The focus is on **running the pretrained CIFAR-10 example quickly**
- Large files over GitHub's regular file size limit were removed from the repository
- Required large assets are provided separately through Dropbox
- A clean **single-GPU generation command** is provided as the main example

---

## 1. Clone This Repository

git clone https://github.com/Pogjunan/DxMI_EasyRun.git

cd DxMI_EasyRun

## 2. Download Required Assets

Go to the **official DxMI repository** below:

https://github.com/swyoon/Diffusion-by-MaxEntIRL

In the official README, you will find Dropbox links for:

- `datasets`
- `pretrained`

Download **both folders completely** and place them in this repository as:

```text
DxMI_EasyRun/
├── datasets
└── pretrained
├── configs
├── datasets
│   ├── cifar-10-batches-py
│   ├── cifar10_train_png
│   ├── cifar10_train_fid_stats.pt
│   └── ...
├── pretrained
│   ├── cifar10_ddpm_dxmi_T10
│   └── ...
├── generate_cifar10.py
└── ...
```

# 3. Additional Large Files Removed from GitHub

Some files were removed from this repository because they are too large to keep in a regular GitHub repository.

I provide the following files separately through Dropbox:https://drive.google.com/drive/folders/1XocMue67OgXwMPdcDTZQ61Wfj2ufHNd6?usp=drive_link

(1) **generated.npz**

Place it at: ```text pretrained/cifar10_ddpm_dxmi_T10/generated.npz ```

This file is a packed *.npz* archive of generated CIFAR-10 samples.

(2) **cifar10_train_png_pil.npz**

```text
./cifar10_train_png_pil.npz
```

This file is a packed .npz archive of CIFAR-10 training images prepared for convenient reuse and evaluation-related workflows.

4. Environment

Recommended environment:

Python >= 3.8

PyTorch >= 2.0

CUDA >= 11.6

Important Note for CIFAR-10

For the CIFAR-10 setup, use:
```python
pip install numpy==1.26.4
```

Install your PyTorch version according to your CUDA environment, then install the remaining dependencies.

# 5. Run Pretrained CIFAR-10 Generation

Use the following command for a clean single-GPU run:

```python
CUDA_VISIBLE_DEVICES=0 \
python -m torch.distributed.run --standalone --nproc_per_node=1 generate_cifar10.py \
  --log_dir pretrained/cifar10_ddpm_dxmi_T10 \
  --stat datasets/cifar10_train_fid_stats.pt \
  --batchsize 100 \
  -n 50000


```

This command will:

- load the pretrained checkpoint automatically

- generate CIFAR-10 samples

- save generated PNG files under:
```text
pretrained/cifar10_ddpm_dxmi_T10/generated
```

