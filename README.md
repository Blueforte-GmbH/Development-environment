# Development-environment
Optimal Data Science environment setup. Idea is to have a seemless environment irrespective of which operating system you use. 

# Contents
- [WSL2](#wsl2)
- Python virtual environments
  - [venv](#python-virtual-environments-with-venv)
  - [Conda](#conda)
  - [Poetry](#poetry)
  
---
# WSL2
Windows Subsystem for Linux (WSL) lets you run a Linux environment inside of your Windows including most command-line tools, utilities, and applications. All this without the overhead of a traditional virtual machine or dual-boot setup.

[Here](https://docs.microsoft.com/en-us/learn/modules/get-started-with-windows-subsystem-for-linux/) is how you get started. 

## Prerequisites
Ensure to turn on these in Windows Features before installing WSL as shown below.
- 1. Virtual Machine Platfomr
- 2. Windows Subsystem for linux


![Image](img/win_features.png)

If the virtual machine is disable in your system, then you need to enable it through Bios. Check here in Task manager. 

![Image](img/virtual.png)


## Drives in WSL 
After installation you can verify the wsl version in powershell as 

```shell
wsl ---version
```

The Windows drives will be reflected in WSL as;
```
$ wsl/mnt/c 
```

## Pro tip
If you plan to work on wsl it is advisible to keep the files in wsl drive i.e `/home/user` instead of `/mnt/c` or `/mnt/d`


## Issues and Debugging
Bash can lose connectivity to internet once connected to a VPN. You need to manually overwrite the DNS resolution which you can find in `/wsl/resolv.conf`. 
Check [here](https://docs.microsoft.com/en-us/windows/wsl/troubleshooting#bash-loses-network-connectivity-once-connected-to-a-vpn) for more details. 


---

## Python Virtual Environments with `venv`
Installing a specific python version using `venv`

```shell
sudo apt install python3.8-venv    
```

Create a virtual environment with `venv`. 

```shell
python3 -m venv <envname>
```

Activate and deactivate the environment. 
```shell
source <venv>/bin/acivate

# to deactivate
deactivate
```
---
## Conda
Download the version of conda you need as below and install. 

```shell
wget https://repo.anaconda.com/miniconda/Miniconda3-py38_4.10.3-Linux-x86_64.sh

# install the above downloaded file
bash Miniconda3-<version>.sh

# remove the file once finished
rm Miniconda3-<version>.sh
```

Update conda
```shell
conda update conda
```

Creating new environments
```shell
conda create --name <env name>

# activate environment
conda activate <env name>
```

Adding packages to conda
```shell
conda install numpy
```

```
# Install env with different python version. 
conda create --name condaenv python=3.8.10
```

Adding packages form environments `yaml`. 

A `yaml` file needs to be created first as described [here](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html#create-env-file-manually)

```
conda env create -f environments.yml
```

Now update environments based on `yaml` .
```
conda env update --file environments.yml
```



For all commands refer [conda cheat sheet](https://docs.conda.io/projects/conda/en/latest/user-guide/cheatsheet.html)

---

## Poetry
![Image](img/poetry_isin.png)


Install poetry with `curl`. 

```shell
curl -sSL https://raw.githubusercontent.com/python-poetry/poetry/master/get-poetry.py | python -
```

If python not found, replace it with `python3`
```shell
curl -sSL https://raw.githubusercontent.com/python-poetry/poetry/master/get-poetry.py | python3 -
```

Initialise an environment. This automatically created `.toml` file in the directory with all packages. 
```
poetry init
```

Once initialised, install or update if already installed. 
```
poetry install

# in case of an update
poetry update
```

Adding packages to your project ? Just do 
```
poetry add <package name>
```


### Pro Tip
1. *Do not install from `pip`. Always use the `curl` method as above. 
2. Poetry install envs in your `.cache/` directory. This below will install in your working directory

```
poetry config virtualenvs.in-project true
```