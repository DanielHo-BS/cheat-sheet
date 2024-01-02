# Conda

## Introduction

Anaconda是目前最受歡迎的Python數據科學(Data Science)平台，適用於Windows、Linux和MacOS 不同作業系統環境下的conda軟件包(package)和虛擬環境管理器。

## Installation

[Anaconda](https://www.anaconda.com/download/)

[安裝教學 on windows](https://medium.com/python4u/anaconda%E4%BB%8B%E7%B4%B9%E5%8F%8A%E5%AE%89%E8%A3%9D%E6%95%99%E5%AD%B8-f7dae6454ab6)

### On WSL

```bash
#Download Anaconda from web
wget https://repo.anaconda.com/archive/Anaconda3-<version>-Linux-x86_64.sh

#Install
bash Anaconda3-<version>-Linux-x86_64.sh
# Enter 'yes' to install

#Add PATH
export PATH=/home/<user>/anaconda3/bin:$PATH

#Check version
conda --version
```

## Create enviroment

[建立環境教學](https://medium.com/python4u/%E7%94%A8conda%E5%BB%BA%E7%AB%8B%E5%8F%8A%E7%AE%A1%E7%90%86python%E8%99%9B%E6%93%AC%E7%92%B0%E5%A2%83-b61fd2a76566)

```bash
conda create --name <env-name> python=<version>
```

## Common

### Activate

```bash
activate <env-name>
```

### Deactivate

```bash
deactivate
```

### Install package

```bash
pip install <package-you-want>
```

### Remove

```bash
conda remove --name <env-name> <package>
```

## Warning

There was an error checking the latest version of pip.

```bash
sudo python3 -m pip install --upgrade pip
pip install --upgrade pip
```

## Bash Script

Set up the environment with ``Bash``:

### Step 1: Create a Conda Environment

```bash
conda create --name my_env
```

### Step2: Write the Bash Script: ``setup.sh``

```bash
# Set the conda environment
source ~/anaconda3/etc/profile.d/conda.sh
conda activate my_env
clear
```

### Step3: Run the Bash Script

```bash
# Using 'bash' to keep current environmnet of terminal
bash setup.sh

# Using 'source' to change environmnet of terminal
source setup.sh
```
