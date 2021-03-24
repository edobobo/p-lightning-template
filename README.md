<h1 align="center">
  PyTorch Lightning Template
</h1>

<p align="center">
  <a href="https://pytorch.org/get-started/locally/"><img alt="PyTorch" src="https://img.shields.io/badge/PyTorch-orange?style=for-the-badge&logo=pytorch"></a>
  <a href="https://pytorchlightning.ai/"><img alt="Lightning" src="https://img.shields.io/badge/-Lightning-blueviolet?style=for-the-badge"></a>
  <a href="https://hydra.cc/"><img alt="Config: hydra" src="https://img.shields.io/badge/config-hydra-blue?style=for-the-badge"></a>
  <a href="https://black.readthedocs.io/en/stable/"><img alt="Code style: black" src="https://img.shields.io/badge/code%20style-black-black.svg?style=for-the-badge"></a>
</p>

<h3 align="center">
  A simple template to bootstrap your PyTorch Lightning project
</h3>

This is a template to initialize [PyTorch](https://pytorch.org) projects that use as a backbone
framework [PyTorch Lightning](https://www.pytorchlightning.ai). The project 
is very simple and minimalistic and serves as a bootstrap in order to avoid rewriting the same
boilerplate code every time a new project is created. Finally, in order to organize the configuration files 
and all the hyperparameters we utilize [Hydra](https://hydra.cc), a framework from 
Facebook Research built for "*elegantly configuring complex applications*".

## Repository Structure
```
p-lightning-template
| conf                      # contains Hydra config files
  | data
  | model
  | train
  root.yaml                 # hydra root config file
| data                      # datasets should go here
| experiments               # where the models are stored
| src
  | pl_data_modules.py      # base LightinigDataModule
  | pl_modules.py           # base LightningModule
  | train.py                # main script for training the network
| README.md
| requirements.txt
| setup.sh                  # environment setup script 
```
The structure of the repository is very simplistic and involves mainly four
components:
- **pl_data_modules.py** where you can declare your LightningDataModules.
- **pl_modules.py** where you can declare your LightningModules.
- **train.py** the main script to start the training phase.
- **conf** the directory containing the config files of Hydra.

## Initializing the environment
In order to set up the python interpreter we utilize [conda](https://docs.conda.io/projects/conda/en/latest/index.html)
, the script `setup.sh` creates a conda environment and install pytorch
and the dependencies in "requirements.txt".


## Using the repository
To use this repository as a starting template for your projects, you can just click the green button "Use this template" at the top of this page. More on using GitHub repositories on the following [link](https://docs.github.com/en/github/creating-cloning-and-archiving-repositories/creating-a-repository-from-a-template#creating-a-repository-from-a-template).


## FAQ
**Q**: When I run any script using a Hydra config I can see that relative paths do not work. Why?

**A**: Whenever you run a script that uses a Hydra config, Hydra will create a new working directory
(specified in the root.yaml file) for you. Every relative path you will use will start from it, and this is why you 
get the 'FileNotFound' error. However, using a different working directory for each of your experiments has a couple of 
benefits that you can read in the 
[Hydra documentation](https://hydra.cc/docs/tutorials/basic/running_your_app/working_directory/) for the Working 
directory. There are several ways that hydra offers as a workaround for this problem here we will report the two that
the authors of this repository use the most, but you can find the other on the link we previously mentioned:

1. You can use the 'hydra.utils.to_absolute_path' function that will convert every relative path starting from your 
working directory (p-lightning-template in this project) to a full path that will be accessible from inside the 
new working dir.
   
2. Hydra will provide you with a reference to the original working directory in your config files.
You can access it under the name of 'hydra:runtime.cwd'. So, for example, if your training dataset
has the relative path 'data/train.tsv' you can convert it to a full path by prepending the hydra 
variable before 


## Contributing
Contributions are always more than welcome, the only thing to take into account when submitting a pull request is
that we utilize the [Black](https://github.com/psf/black) code formatter with a max length for the code of 120. 
More pragmatically you should ensure to utilize the command "black -l 120" on the whole "src" directory before pushing
the code. 


## Other useful repositories
This repository has been created with the idea of providing a simple skeleton from which you can 
start a PyTorch Lightning project. Instead of favoring the customizability, we favored the simplicity
and we intended this template as a base for building more specific templates based on the user needs
(for example by forking this one). However, there are several other repositories with different 
features that you can check if interested. We will list two of them here:
- [lucmos/nn-template](https://github.com/lucmos/nn-template): a very nice template with support for
    DVC.
- [hobogalaxy/lightning-hydra-template](https://github.com/hobogalaxy/lightning-hydra-template):
    another useful and very well documented template repository.

As we were mentioning earlier we created this repository even with the intention of bootstrapping
other Lightning templates. We mention here these repositories:
- [poccio/grid-seq2seq](https://github.com/poccio/grid-seq2seq): This is a NLP oriented repository 
  that serves as a skeleton for Seq2Seq projects, while at the same time offering a way of running 
  Bart based Seq2Seq models without writing a single line of code!
it in the yaml files by doing that following: '${hydra:runtime.cwd}/data/train.tsv'.
  
