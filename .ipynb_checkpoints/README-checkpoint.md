# DxMI_EasyRun

Easy-to-run version of **DxMI** for pretrained CIFAR-10 generation.

This repository is a simplified setup for running the pretrained CIFAR-10 generation pipeline from the official DxMI project without having to manually reconstruct every file and folder by yourself.

## Official Source

This project is based on the official DxMI repository:

- **Official DxMI repository**: https://github.com/swyoon/Diffusion-by-MaxEntIRL
- **Paper**: *Maximum Entropy Inverse Reinforcement Learning of Diffusion Models with Energy-Based Models*

Please refer to the official repository for the full paper implementation, training setups, and additional experiments.

---

## What is Different in This Repository?

This repository is organized for **easy execution**.

- The focus is on **running the pretrained CIFAR-10 example quickly**
- Large files over GitHub's regular file size limit were removed from the repository
- Required large assets are provided separately through Dropbox
- A clean **single-GPU generation command** is provided as the main example

---

## 1. Clone This Repository

```bash
git clone https://github.com/Pogjunan/DxMI_EasyRun.git
cd DxMI_EasyRun