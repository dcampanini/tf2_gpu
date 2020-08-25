# Working with Tensorflow and GPU
This repo describes the steps to setting a conda environment to work with tensorflow>= 1.13.0 and gpu on Ubuntu 18.04 or 16.04

## Delete previous CUDA and NVIDIA programs
- For this I followed the next web page https://medium.com/@exesse/cuda-10-1-installation-on-ubuntu-18-04-lts-d04f89287130

> These are the instruction to delete CUDA and NVIDIA programs

```shell
$ sudo rm /etc/apt/sources.list.d/cuda*
$ sudo apt remove --autoremove nvidia-cuda-toolkit
$ sudo apt remove --autoremove nvidia-*
```

## Install NVIDIA requirements
- For this I followed the next web page https://www.tensorflow.org/install/gpu

> Ubuntu 18.04 (CUDA 10.1)

```shell
# Add NVIDIA package repositories
$ wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/cuda-repo-ubuntu1804_10.1.243-1_amd64.deb
$ sudo apt-key adv --fetch-keys https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/7fa2af80.pub
$ sudo dpkg -i cuda-repo-ubuntu1804_10.1.243-1_amd64.deb
$ sudo apt-get update
$ wget http://developer.download.nvidia.com/compute/machine-learning/repos/ubuntu1804/x86_64/nvidia-machine-learning-repo-ubuntu1804_1.0.0-1_amd64.deb
$ sudo apt install ./nvidia-machine-learning-repo-ubuntu1804_1.0.0-1_amd64.deb
$ sudo apt-get update

# Install NVIDIA driver
$ sudo apt-get install --no-install-recommends nvidia-driver-450
# Reboot. Check that GPUs are visible using the command: nvidia-smi

# Install development and runtime libraries (~4GB)
$ sudo apt-get install --no-install-recommends \
    cuda-10-1 \
    libcudnn7=7.6.5.32-1+cuda10.1  \
    libcudnn7-dev=7.6.5.32-1+cuda10.1


# Install TensorRT. Requires that libcudnn7 is installed above.
$ sudo apt-get install -y --no-install-recommends libnvinfer6=6.0.1-1+cuda10.1 \
    libnvinfer-dev=6.0.1-1+cuda10.1 \
    libnvinfer-plugin6=6.0.1-1+cuda10.1
```

## Activate a conda evironment 
- Activate a conda environmet from environmet.yml with all the packages to work with tensorflow >=2.0 and gpu
```
$ git clone https://github.com/dcampanini/tf2_gpu
$ cd tf2_gpu
$ conda env create -f environment.yml
$ conda activate name_environment
```

> The first line of the yml file sets the new environment's name

Now you can train a model with tensorflow on gpu