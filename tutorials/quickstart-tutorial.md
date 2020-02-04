---
layout: page
title: Quick-start tutorial for Google Cloud and Jupyter notebooks
permalink: /tutorials/quickstart/
---

# Getting started
In this class, we will use [Jupyter notebooks](http://jupyter.org/) for all the assignments. Jupyter notebooks provide a web browser-based programming enviroment where you can execude code in blocks, display the output figure, and annotate in Markdown *in situ*. With these properties, it's been widely used in the scientific community to make research project reproducible. You can work on your assignment either **locally** or on a virtual machine through [**Google Cloud**](https://cloud.google.com/). The following instructions will give you a quick-start guide for both ways. 

## Working from Google Cloud

Deep learning tends to require extremely large networks and millions if not billions of training points, so for this class we will be using the Google Cloud Platform to run and store our models (which can then be transferred locally). You will each be provided with a coupon for $50, which roughly translates to 5 hours of compute time/week. You will use the same account for the entire semester - including the final project - so don't spend it all in one place!

## Set up a Google Cloud project

### Redeem your Google Cloud education grant
You can do this either by clicking on "Redeem now" in the email coupon, or by visiting this [link](https://console.cloud.google.com/edu) and entering the code from the email. Click "Accept and continue" to accept the terms. Your account should now have a $50 credit.

### Create a new project 

- Go to [Google Cloud Resource Manager](https://console.cloud.google.com/cloud-resource-manager?_ga=2.57885226.-1229808733.1579820986) (you must be signed in on Google)
- Click "CREATE PROJECT"
- Enter a project name
- Select "Computational Systems Biology: Deep Learning" as the billing account, if it is not already selected
- Click "Create"
- The project will be given a unique project id e.g. affable-ring-631231. Remember this id for a later step.

More information for creating, updating, or deleting a Cloud Platform project can be found [here](https://cloud.google.com/resource-manager/docs/creating-managing-projects). 

### Enable the Google Compute Engine and Cloud Source Repositories APIs for the project

- Go to the enable APIs [webpage](https://console.cloud.google.com/flows/enableapi?apiid=compute,sourcerepo.googleapis.com&redirect=https://console.cloud.google.com&_ga=2.265664271.-1250025688.1579822842)
- Select the project you just created
- Click "Continue"
- Wait for the APIs to be enabled (it may take awhile). The page should change, and you should hit "Continue" again.

### Install and initialize the Cloud SDK

The Cloud SDK is a set of command line tools that allow you to manage resources and applications hosted on Google Cloud Platform. The following is an abbreviated version of the installation instructions available [here](https://cloud.google.com/sdk/docs/), which should be sufficient for most users.

#### Windows
- Download the Cloud SDK installer [here](https://dl.google.com/dl/cloudsdk/channels/rapid/GoogleCloudSDKInstaller.exe)
- Launch the installer and follow the prompts
- After installation has completed, accept the following options
	- Start Cloud SDK Shell
	- Run gcloud init
- A terminal should pop up. Follow the prompts to complete the installation:
	- Log in when prompted (the login window will pop up in your browser, log in using your Google account)
	- Pick the cloud project to use, using the unique id assigned to the project you just created (see the Create a new project section)
	- Set the default "Compute Region and Zone" to "us-east1-b"

#### MacOS and Linux
- Download the Cloud SDK for MacOS [google-cloud-sdk-277.0.0-darwin-x86_64.tar.gz](https://dl.google.com/dl/cloudsdk/channels/rapid/downloads/google-cloud-sdk-277.0.0-darwin-x86_64.tar.gz) or for Linux [google-cloud-sdk-277.0.0-linux-x86_64.tar.gz](https://dl.google.com/dl/cloudsdk/channels/rapid/downloads/google-cloud-sdk-277.0.0-linux-x86_64.tar.gz)
- Extract the file to your preferred installation location. There should now be a new folder named "google-cloud-sdk"
- Add the Cloud SDK to your path
	- Open a terminal and navigate to the directory containing the new "google-cloud-sdk" directory
	- Run the following command and follow the on-screen instructions. Hitting enter for all prompts should generally be sufficient.
		```
		./google-cloud-sdk/install.sh
		```
- Initialize the SDK 
	- Open a ***new*** terminal and run the command
		```
		gcloud init
		```
	- Log in when prompted (the login window will pop up in your browser, log in using your Google account)
	- Pick the cloud project to use, using the unique id assigned to the project you just created (see the Create a new project section)
	- Set the default "Compute Region and Zone" to "us-east1-b"


## Set up a Cloud Datalab

We will make heavy use of Jupyter notebooks in this class for the sake of presentation and reproducibility of results. The easiest way to do this in the Google Cloud Platform is by setting up a VM instance to run Cloud Datalab Notebooks. 

### Install datalab with gcloud
Run the following, saying yes to all prompts
```
gcloud components update
gcloud components install datalab
```

### Create a datalab instance
Create a Datalab instance with just CPUs
```
datalab create ps1-datalab
```

Alternatively, you can create one with GPUs (could be useful for ps2 and ps3):
```
datalab beta create-gpu ps1-datalab
```

### Run a Jupyter Notebook on the Datalab instance
In your browser, navigate to http://localhost:8081 

Now, upload the Jupyter notebook you want to run to the datalab instance via the “Upload” button.

### Close the Datalab instance
Finally, when you are done, you can kill the active command. Then, delete the instance to avoid further billing with: 
```
datalab delete --delete-disk ps1-datalab
```
NOTE: Ensure you have downloadeded your work before deleting the instance. 

You can visit the [Google Cloud Console](https://console.cloud.google.com/) for an overview of your cloud environment e.g. to view billing information.

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
