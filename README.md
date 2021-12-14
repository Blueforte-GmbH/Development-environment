# Development-environment
Optimal Data Science environment setup. Idea is to have a seemless environment irrespective of which operating system you use. 

# Topics
- WSL2
- Python virtual environments
  - venv
  - Conda
  - Poetry
  

## Virtual Environments with `venv`
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

## Conda

```shell
wget https://repo.anaconda.com/miniconda/Miniconda3-py38_4.10.3-Linux-x86_64.sh

bash Miniconda3-<version>.sh
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

# adding packages to conda
```shell
conda install numpy
```

```
### Install env with different python version. 
conda create --name condaenv python=3.8.10
```

For all commands refer [conda sheet sheet](https://docs.conda.io/projects/conda/en/latest/user-guide/cheatsheet.html)
---

## Poetry
Install poetry with `curl` and not by `pip`. 

```shell
curl -sSL https://raw.githubusercontent.com/python-poetry/poetry/master/get-poetry.py | python -
```

If python not found, replace it with `python3`
```shell
curl -sSL https://raw.githubusercontent.com/python-poetry/poetry/master/get-poetry.py | python3 -
```
