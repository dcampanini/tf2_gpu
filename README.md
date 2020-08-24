# tf2_gpu
Install CUDA 10 to work with Tensorflow  >= 1.13.0 on Ubuntu 16.04 and 18.04

## Delete CUDA and NVIDIA programs

- For this I follow the next web page https://medium.com/@exesse/cuda-10-1-installation-on-ubuntu-18-04-lts-d04f89287130

> These are the instruction to delete CUDA and NVIDIA programs

```shell
$ sudo rm /etc/apt/sources.list.d/cuda*
$ sudo apt remove --autoremove nvidia-cuda-toolkit
$ sudo apt remove --autoremove nvidia-*
```