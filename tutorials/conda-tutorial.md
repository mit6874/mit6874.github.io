---
layout: page
title: Conda Tutorial
permalink: /tutorials/conda-tutorial/
---

Conda is a powerful package management software for Python. It's widely used in the scientific community and in data science platforms such as [Anaconda](https://www.anaconda.com/).

With conda, we can create "enviroments", or bundles of packages of particular versions, that are designed for each specific application or use case.

******************
**If you take this course for credit and thus running on Google Cloud, you don't need conda**.
******************


## Install conda

Simply follow the instructions [here](http://docs.anaconda.com/anaconda/install/) to install conda (Python 3 version). You can verify installation by `conda list`, and you should be able to see a list of packages installed.

Along with conda, Python and pip has also been installed. You can verify by `which python` and `which pip`, and you should find the path under a folder called "miniconda3/bin". This also means that all of your previously installed packages will NOT be used anymore as they are not managed by conda.

However, the previously installed packages are still there. To use the system Python and pip, simply do `/usr/bin/python` or `/usr/bin/pip`.

## Basic management with conda
Here we list a few most commonly used commands. For more details, please refere to the official documentation.

#### List all the packages installed

```bash
conda list
```
	
#### Install a package (e.g. numpy), optionally with a version number

```bash
## Either works
conda install numpy
pip install numpy
```

#### Install TensorFlow (using pip)

Install TensorFlow with pip instead of conda (pip TensorFlow packages are more recent).

See [TensorFlow docs](https://www.tensorflow.org/install/pip).


#### Create an enviroment named "myenv" with numpy and scipy installed

```bash
conda create --name myenv numpy scipy
```

#### Create an environment according to a spefication yaml file (which we will provide for you for each pset)

```bash
conda env create -f pset1_env.yml
```
The actual name of the enviroment can be found in the yaml file.


#### Activate an environment named "myenv"

```bash
source activate myenv
```

#### Deactivate the current environment

```bash
source deactivate
```

