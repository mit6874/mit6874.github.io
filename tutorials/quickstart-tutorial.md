---
layout: page
title: Quick-start tutorial for Google Cloud and Jupyter notebooks
permalink: /tutorials/quickstart/
---

# Getting started
In this class, we will use [Jupyter notebooks](http://jupyter.org/) for all the
assignments. Jupyter notebooks provide a web browser-based programming enviroment where you can execude code in blocks, display the output figure, and annotate in Markdown *in situ*. With these properties, it's been widely used in the scientific community to make research project reproducible. You can work on your assignment either **locally** or on a virtual machine
through [**Google Cloud**](https://cloud.google.com/). The following instructions will give you a quick-start guide for both ways. 

## Working from Google Cloud
Deep learning requires lots of computational resources, so for this class we introduce the Google Cloud Platform to run and store your models for your convenience. You will each be provided with a coupon for $50, which roughly translates to 5 hours of compute time/week. You will use the same account for the entire semester - including the final project - so don't spend it all in one place!

### First time using Google Cloud:
* Redeem your Google Cloud education grant with the coupon emailed to you before class. Use your own gmail account to log in to the Google Cloud console.
* Create a GCP project, enable billing and APIs following instructions [here](https://cloud.google.com/datalab/docs/quickstart#before-you-begin).
* Install and initialize the Cloud SKD following instructions [here](https://cloud.google.com/sdk/docs/). You only need to initialize it once by running (the login window will pop up in your browser, log in using your gmail account and complete the rest of the steps from your command line as prompted): 
```bash
gcloud init
```
For Windows users, add the full path to `google-cloud-sdk\bin` into your `PATH` variable before using datalab command. 

### Set up and launch Cloud Datalab
Following instructions [here](https://cloud.google.com/datalab/docs/quickstart#steps_to_set_up_and_open_cloud_datalab). Install `datalab` with gcloud:
```bash
gcloud components update
gcloud components install datalab
```
Then create a datalab instance 
```bash
datalab create datalab-instance-name
```
After selecting a zone (pick any number from the shown list), it will initialize the instance and establish an SSH access automatically for you. Once prompted, point your web browser at [http://localhost:8081](http://localhost:8081) to
start using datalab. If everything worked correctly, you should see a screen like this:

<div class='fig figcenter'>
  <img src='/assets/googlecloud.png'>
</div>

Click *upload* to upload the homework materials to your datalab and start working on your problem sets by clicking through `***.ipynb`.


### Pricing
There is no charge for using Google Cloud Datalab. However, you do pay for any Google Cloud Platform resources you use with Cloud Datalab (compute and storage resources, etc.). E.g. you incur costs from the time of creation to the time of deletion of the Cloud Datalab VM instance. **Keep in mind that you only have limited budget with $125 coupon so don't let your instance run forever!**

### Stopping an instance
Run the following command to stop your Cloud Datalab instance to avoid incurring unnecessary costs when you want to pause using Cloud Datalab
```bash
datalab stop instance-name
```
When you are ready to start using Cloud Datalab again (or if your terminal command window is closed or interrupted while running datalab and you want to reconnect), run `datalab connect instance-name` command to restart the instance. You can also stop, restart, and manage your VM instances in the [Google Compute Engine](https://console.cloud.google.com/compute) any time.

## Working locally
You will need to set up a Python environment and install Jupyter. We strongly recommend using [Anaconda with Python 3.7](https://www.anaconda.com/download/#macos) because it will automatically install Python and Jupyter notebook and help manage packages efficiently.

### Installing Conda
Download and install Anaconda [here](https://www.anaconda.com/download/): https://www.anaconda.com/download/ following the instruction [here](http://docs.anaconda.com/anaconda/install): http://docs.anaconda.com/anaconda/install. We recommend using **Python 3**. 

### Installing Jupyter notebook and other dependencies without Conda
If you already have your own Python environment and don't feel like to use Conda, you can still install Jupyter with `pip`:
```bash
python -m pip install --upgrade pip
python -m pip install jupyter
python -m pip install numpy
python -m pip install matplotlib
python -m pip install scipy
```
OR if you have both Python 2 and Python 3 installed:
```bash
python3 -m pip install --upgrade pip
python3 -m pip install jupyter
python3 -m pip install numpy
python3 -m pip install matplotlib
python3 -m pip install scipy
```

### Installing TensorFlow and dependencies

#### Python 3.7

If you are working with Python 3.7 (which is included in the current Anaconda release), install TensorFlow 1.13 nightly builds.

TensorFlow without GPU support:
```bash
python -m pip install --upgrade tf-nightly
```

TensorFlow with GPU support:

Requires a nVidia graphics card with compute capability >= 6.0, recent nVidia drivers, CUDA 10.0 and cuDNN 7.4.

See [official TensorFlow page about GPU support](https://www.tensorflow.org/install/gpu).
```bash
python -m pip install --upgrade tf-nightly-gpu
```

#### Python 3.6 and older

If you are working with Python 3.6 or older, install TensorFlow 1.12.0 using the following commands:

See [official TensorFlow install instructions](https://www.tensorflow.org/install/pip).

TensorFlow without GPU support:
```bash
python -m pip install --upgrade tensorflow
```

TensorFlow with GPU support:

Requires a nVidia graphics card with compute capability >= 3.0, recent nVidia drivers, CUDA 9.0 and cuDNN >= 7.2.

See [official TensorFlow page about GPU support](https://www.tensorflow.org/install/gpu).
```bash
python -m pip install --upgrade tensorflow-gpu
```

### Running Jupyter notebook
Once you install Anoconda, Jupyter is automatically installed already. You can start the Jupyter server from the homework directory you will be working on with this command:
```bash
jupyter notebook
```
Once Jupyter is running, point your web browser at [http://localhost:8888](http://localhost:8888) to
start using IPython notebooks. If everything worked correctly, you should
see a screen like this, showing all available IPython notebooks in the current
directory:

<div class='fig figcenter'>
  <img src='/assets/ipynotebook.png'>
</div>

Click through the `ps*.ipynb` and start working on your problem set! More tutorials about how to use Jupyter Notebook can be found [here](https://jupyter-notebook.readthedocs.io/en/stable/notebook.html).
