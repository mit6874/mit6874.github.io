---
layout: page
title: Quick-start tutorial for 6.874
permalink: /tutorials/quickstart-tutorial/
---

# Getting started
In this class, we will use [Jupyter notebooks](http://jupyter.org/) for all the
assignments. Jupyter notebooks provide an web browser-based programming enviroment where you can execude code in pieces, display the output figure, and annotate in Markdown *in situ*. With these properties, it's been widely used in the scientific community to make research project reproducible. You can work on your assignment either **locally** or on a virtual machine
through [**Google Cloud**](https://cloud.google.com/). The following instructions will give you a quick-start guide for both ways. 

## Working from Google Cloud
Deep learning requires lot of computational resources, so for this class we introduce Google Cloud Platform to run and store your models for your convenience. You will each be provided with a coupon for $125, which roughly translates to 10 hours of compute time/week. You will use the same account for the entire semester - including the final project - so don't spend it all in one place!

### First time using Google Cloud:
* Redeem your Google Cloud education grant with the coupon from [here](https://console.cloud.google.com/education): https://console.cloud.google.com/education. Use your own gmail account to login the google cloud console.
* Create a GCP project, enable billing and APIs following instructions [here](https://cloud.google.com/datalab/docs/quickstart#before-you-begin): https://cloud.google.com/datalab/docs/quickstart#before-you-begin
* Install and initialize the Cloud SKD following instructions [here](https://cloud.google.com/sdk/docs/): https://cloud.google.com/sdk/docs/. You only need to initialize it once by running (The login window will pop up in your browser, log in using your gmail account and complete the rest of the steps from your command line as prompted): 
```bash
gcloud init
```
### Set up and launch Cloud Datalab
Following instructions [here](https://cloud.google.com/datalab/docs/quickstart#steps_to_set_up_and_open_cloud_datalab): https://cloud.google.com/datalab/docs/quickstart#steps_to_set_up_and_open_cloud_datalab. Install `datalab` with gcloud:
```bash
gcloud components update
gcloud components install datalab
```
Then create a datalab instance 
```bash
datalab create datalab-instance-name
```
After selecting a zone (pick any number from the shown list), it will initialize the instance and establish an SSH access automatically for you. Once prompted, point your web browser at http://localhost:8081 to
start using datalab.If everything worked correctly, you should see a screen like this:

<div class='fig figcenter'>
  <img src='/assets/googlecloud.png'>
</div>

Click *upload* to upload the homework materials to your datalab and start working on Pset 1 by clicking through `mnist_lr.ipynb`.

## Working locally
You will need to set up a python environment and install Jupyter. We strongly recommend using [Anaconda](https://www.anaconda.com/download/#macos) because it will automatically install python and Jupyter notebook and help manage packages efficiently.
### Installing Conda
Download and install Anaconda [here](https://www.anaconda.com/download/): https://www.anaconda.com/download/ following the instruction [here](http://docs.anaconda.com/anaconda/install): http://docs.anaconda.com/anaconda/install. We recommend using **python 2.7** version, but you can always switch to python 3 using conda environmnet. 
### Installing Jupyter notebook without Conda
If you already have your own python environment and don't feel like to use Conda, you can still install Jupyter with `pip`:
```bash
python -m pip install --upgrade pip
python -m pip install jupyter
```
OR if you Python 3 installed:
```bash
python3 -m pip install --upgrade pip
python3 -m pip install jupyter
```
### Running Jupyter notebook
Once you install Anoconda, jupyter is automatically installed already. You can start the jupyter server from the homework directory you will be working on with this command:
```bash
jupyter notebook
```
Once Jupyter is running, point your web browser at http://localhost:8888 to
start using IPython notebooks. If everything worked correctly, you should
see a screen like this, showing all available IPython notebooks in the current
directory:

<div class='fig figcenter'>
  <img src='/assets/ipynotebook.png'>
</div>

Click through the `mnist_lr.ipynb` and start working on your Pset 1! More tutorials about how to use Jupyter Notebook can be found [here](https://jupyter-notebook.readthedocs.io/en/stable/notebook.html): https://jupyter-notebook.readthedocs.io/en/stable/notebook.html.
