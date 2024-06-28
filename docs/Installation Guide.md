# Installation Guide

- [Installation Guide](#installation-guide)
  - [1. Prerequisites](#1-prerequisites)
    - [1.1 Install Nvidia GPU Driver](#11-install-nvidia-gpu-driver)
    - [1.2 Install NVIDIA CUDA Compiler (NVCC)](#12-install-nvidia-cuda-compiler-nvcc)
  - [2. Install Python Requirements](#2-install-python-requirements)

## 1. Prerequisites
The hardware specifications in this experiment are as follow:
| <center>**Component** | <center>**Details**                            |
| --------------------- | ---------------------------------------------- |
| CPU                   | Intel Core i9-10900 CPU @ 2.80GHz              |
| GPU                   | 8GB GDDR6 - GeForce® RTX 2080 SUPER™ VENTUS OC |
| Memory                | 16 GB                                          |
| Storage               | 8TB HDD - Seagate Firecuda  ST8000DX001        |
| OS                    | Ubuntu 22.04.4 LTS                             |


### 1.1 Install Nvidia GPU Driver
1. Get the latest drivers:
    ```bash
    sudo add-apt-repository ppa:graphics-drivers/ppa
    sudo apt update
    ```
2. Install the ubuntu-drivers:
    ```bash
    sudo ubuntu-drivers autoinstall
    ```
3. Reboot your system:
    ```
    sudo reboot
    ```
4. Verify the installation:
    ```bash
    nvidia-smi
    ```
    **Output**:
    ```console
    Thu Jun 27 16:51:58 2024       
    +-----------------------------------------------------------------------------------------+
    | NVIDIA-SMI 555.42.02              Driver Version: 555.42.02      CUDA Version: 12.5     |
    |-----------------------------------------+------------------------+----------------------+
    | GPU  Name                 Persistence-M | Bus-Id          Disp.A | Volatile Uncorr. ECC |
    | Fan  Temp   Perf          Pwr:Usage/Cap |           Memory-Usage | GPU-Util  Compute M. |
    |                                         |                        |               MIG M. |
    |=========================================+========================+======================|
    |   0  NVIDIA GeForce RTX 2080 ...    Off |   00000000:01:00.0 Off |                  N/A |
    | 25%   29C    P8              7W /  250W |       6MiB /   8192MiB |      0%      Default |
    |                                         |                        |                  N/A |
    +-----------------------------------------+------------------------+----------------------+
                                                                                            
    +-----------------------------------------------------------------------------------------+
    | Processes:                                                                              |
    |  GPU   GI   CI        PID   Type   Process name                              GPU Memory |
    |        ID   ID                                                               Usage      |
    |=========================================================================================|
    |    0   N/A  N/A      1461      G   /usr/lib/xorg/Xorg                              4MiB |
    +-----------------------------------------------------------------------------------------+    
    ```

### 1.2 Install NVIDIA CUDA Compiler (NVCC)
1. Download the CUDA Toolkit 12.2 and select the Linux distribution from [CUDA Toolkit Archive](https://developer.nvidia.com/cuda-toolkit-archive) page, architecture, version, and installer type. For Ubuntu, you might select a `.deb` package for easier installation.
2. Assuming you've downloaded a `.deb` package, you can install it using the following commands. Replace `cuda-repo-<distro>_<version>_amd64.deb` with the actual file name of the downloaded package.
    ```bash
    cd /path/to/download/
    sudo dpkg -i cuda-repo-<distro>_<version>_amd64.deb
    sudo apt-key adv --fetch-keys http://developer.download.nvidia.com/compute/cuda/repos/<distro>/x86_64/7fa2af80.pub
    sudo apt-get update
    sudo apt-get install cuda-12-2
    ```
3. Setup the environment variables, add the following lines to the end of your `~\.bashrc` file:
    ```bash
    export PATH=/usr/local/cuda-12.2/bin${PATH:+:${PATH}}
    export LD_LIBRARY_PATH=/usr/local/cuda-12.2/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}
    ```
    Then, source your `~/.bashrc` to apply the changes:
    ```bash
    source ~/.bashrc
    ```

## 2. Install Python Requirements
1. Install [Python](https://www.python.org/downloads/). Verify the Python installation using `python --version`.<br>
    **Output**:
    ```console
    Python 3.10.12
    ```
2. On the project folder, create Python Virtual Environment:
   1. Create venv:
        ```bash
        python -m venv venv
        ```
    2. Activate venv, then your terminal should shown `(venv)` later:
        - Windows:
            ```bash
            venv\Scripts\activate
            ```
        - Linux/MacOS:
            ```bash
            source ./venv/bin/activate
            ```
            **Output** (You can see the `(venv)` word in the beginning of your terminal line):
            ```console
            (venv) wifi@bmw-ntust:~/Documents/GitHub/nvidia-sionna$ 
            ```
3. Install all Python dependencies from [venv.yml](../venv.yml) in this repository:
    ```bash
    pip install -r venv.yml
    ```
    Verify your installation using `pip list` and check whether it's the same with [venv.yml](../venv.yml) or not.
4. Test the NVIDIA Sionna installation in Python:
    ```bash
    python
    ```
    In Python terminal:
    ```python
    import sionna
    print(sionna.__version__)
    ```
    **Output**:
    ```bash
    0.18.0
    ```
5. To verify the functionality of Sionna, execute the [Hello_world.ipynb](./Hello_World.ipynb) notebook.