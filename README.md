# ReadMe

## Description

This is a demo program of [PatchRNN](https://shuwang127.github.io/PatchRNN-demo), which identifies security patches using recurrent neural networks. The code changes in patches are processed using a twin RNN network, while the commit message is processed with a TextRNN network. Afterward, the information from the commit message and the code revision is fused in order to get the final prediction using a multi-layer perceptron.

More details about the PatchRNN can be found in the paper "[PatchRNN: A Deep Learning-Based System for Security Patch Identification](https://arxiv.org/pdf/2108.03358.pdf)", to appear in the MILCOM 2021, San Diego, USA, November 29–December 2, 2021.

To cite our work, please use
```bibtex
@INPROCEEDINGS{PatchRNN2021Wang,
  author={Wang, Xinda and Wang, Shu and Feng, Pengbin and Sun, Kun and Jajodia, Sushil and Benchaaboun, Sanae and Geck, Frank},
  booktitle={MILCOM 2021 - 2021 IEEE Military Communications Conference (MILCOM)}, 
  title={PatchRNN: A Deep Learning-Based System for Security Patch Identification}, 
  year={2021},
  volume={},
  number={},
  pages={595-600},
  doi={10.1109/MILCOM52596.2021.9652940}}
```

This demo program is base on the [PatchRNN Developer Edition (S2020.08.08-V4)](https://github.com/shuwang127/PatchRNN), developed by [Shu Wang](https://shuwang127.github.io/).

You can also visit PatchRNN official website: [https://shuwang127.github.io/PatchRNN-demo/](https://shuwang127.github.io/PatchRNN-demo/).

## How to run PatchRNN-demo

### 1. Install OS

We use Ubuntu 20.04.2.0 LTS (Focal Fossa) desktop version. \
Download Link: https://releases.ubuntu.com/20.04/ubuntu-20.04.2.0-desktop-amd64.iso

The virtualization software in our experiments is VirtualBox 5.2.24. \
Download Link: https://www.virtualbox.org/wiki/Download_Old_Builds_5_2. \
You can use other software like VMware Workstation.

**System configurations:**\
RAM: 2GB\
Disk: 25GB\
CPU: 1 core in i7-7700HQ @ 2.8GHz

### 2. Download the source code from github

We use `home` directory to store the project folder.

```shell scripts
cd ~
```

Install `git` tool.

```shell scripts
sudo apt install git
```

Download `PatchRNN-demo` project to local disk. (You may need to enter your github account/password.)

```shell scripts
git clone https://github.com/shuwang127/PatchRNN-demo
```

### 3. Install the dependencies.

Install `pip` tool for `python3`.

```shell scripts
sudo apt install python3-pip
```

Install common dependencies.

```shell scripts
pip3 install nltk==3.3
pip3 install natsort
pip3 install pandas
pip3 install sklearn
```

Install CPU-version PyTorch. Official website: https://pytorch.org/.

```shell scripts
pip3 install torch==1.7.1+cpu torchvision==0.8.2+cpu torchaudio==0.7.2 -f https://download.pytorch.org/whl/torch_stable.html
```

Install `clang` tool.

```shell scripts
pip3 install clang==6.0.0.2
```

Configurate the clang environment.

```shell scripts
sudo apt install clang
cd /usr/lib/x86_64-linux-gnu/
sudo ln -s libclang-*.so.1 libclang.so
```

### 4. Run the demo program.

```shell scripts
cd ~/PatchRNN-demo/
python3 demo.py
```

There are 56 input test samples stored in `~/PatchRNN-demo/testdata/`, the output results are saved in `~/PatchRNN-demo/results/results.txt`.

```shell scripts
cat results/results.txt
```

You can find the results.

```shell scripts
.//testdata/nginx/release-1.19.0_release-1.19.1/0a683fdd.patch,1
.//testdata/nginx/release-1.19.0_release-1.19.1/1bbc37d3.patch,1
.//testdata/nginx/release-1.19.0_release-1.19.1/2afc050b.patch,0
.//testdata/nginx/release-1.19.0_release-1.19.1/2d4f04bb.patch,0
.//testdata/nginx/release-1.19.0_release-1.19.1/6bb43361.patch,1
...
```
