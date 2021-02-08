# Pytorch Lightning Project Template

This is a template to initialize [PyTorch](https://pytorch.org) projects that use as a backbone
framework [PyTorch Lightning](https://www.pytorchlightning.ai). The project 
is very simple and minimalistic and serves as a bootstrap in order to avoid rewriting the same
boilerplate code every time a new project is created. Finally, in order to organize the configuration files 
and all the hyperparameters we utilize [Hydra](https://hydra.cc), a framework from 
Facebook Research built for "*elegantly configuring complex applications*".

## Repository Structure
```
p-lightning-template
| conf  # contains Hydra config files
  | data
  | model
  | train
  root.yaml  # hydra root config file
| data  # datasets should go here
| experiments  # where the models are stored
| src
  | pl_data_modules.py  # base LightinigDataModule
  | pl_modules.py  # base LightningModule
  | train.py  # main script for training the network
| README.md
| requirements.txt
| setup.sh # environment setup script 
```
The structure of the repository is very simplistic and involves mainly four
components:
- **pl_data_modules.py** where you can declare your LightningDataModules.
- **pl_modules.py** where you can declare your LightningModules.
- **train.py** the main script to start the training phase.
- **conf** the dircetory containing the config files of Hydra.

## Initialize environment
In order to set up the python interpreter we utilize [conda](https://docs.conda.io/projects/conda/en/latest/index.html)
, the script setup.sh creates a conda environment and install pytorch
and the dependencies in "requirements.txt". 

## Run
All the paths in the project are relative to the 'p-lightning-template' 
repository, thus in order to run the "train.py" script you should properly 
set the PYTHONPATH and launch it from the main directory:
```
PYTHONPATH=$(pwd) python train.py ...
```
