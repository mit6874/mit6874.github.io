# Getting Started with the Google Cloud Platform

Deep learning tends to require extremely large networks and millions if not billions of training points, so for this class we will be using the Google Cloud Platform to run and store our models (which can then be transferred locally). You will each be provided with a coupon for $125, which roughly translates to 10 hours of compute time/week. You will use the same account for the entire semester - including the final project - so don't spend it all in one place!

## Set up a Google Cloud project

* Create an new project 

	First go to [Google Cloud Platform Console](https://console.cloud.google.com/?_ga=1.267732365.202261637.1485992828)(you must be signed in on Google). Then click "Create project" (see the screenshot below). Enter a project name and click "Create". When you create a project you will be given a project id (something that looks like "pro-bliss-156604") and a project number (something that looks like #222531386190)
	
	More information for creating, updating, or deleting a Cloud Platform project can be found [here](https://cloud.google.com/resource-manager/docs/creating-managing-projects). 

	<img src="http://i.imgur.com/DfAAJjA.png" alt="Google Cloud Platform Startpage" width="75%">

* [Redeem your Google Cloud education grant](https://console.cloud.google.com/education)

* [Enable billing for the project](https://support.google.com/cloud/answer/6293499#enable-billing). 

	If this is your first time creating a project, you will be automatically prompted to choose a billing account to link to the project. If not, you can always navigate to and enable billing from the sidebar as below.

	<img src="http://i.imgur.com/O6DO4Yj.png" alt="Billing on the Sidebar" width="75%">

* Enable the Google Compute Engine (GKE) in [API Manager](https://console.cloud.google.com/apis/).

* [Install and initialize the Cloud SDK](https://cloud.google.com/sdk/docs/). 

	The Cloud SDK is a set of command line tools that allow you to manage resources and applications hosted on Google Cloud Platform.

## Set up a Cloud Datalab

We will make heavy use of Jupyter notebooks in this class for the sake of presentation and reproducibility of results. The easiest way to do this in the Google Cloud Platform is by setting up a VM instance to run Cloud Datalab Notebooks. 

* Set up

	We will be following the instructions [here](https://cloud.google.com/datalab/docs/quickstarts/quickstart-gcp-frontend) under "Create a Compute Engine VM on Google Cloud Platform" to set up and run Cloud Datalabs.
	
	**Windows users need to remove the back slashes and make the command one line**
	
	1. First, create a network to hold your datalab servers:
	
		```
		gcloud compute networks create datalab-network \
			--project [PROJECT_ID] \
			--description "Network for Datalab servers"
		```
		
	2. Next, allow SSH access to the network:
	
		```
		gcloud compute firewall-rules create datalab-network-allow-ssh \
			--project [PROJECT_ID] \
			--allow tcp:22 \
			--network datalab-network \
			--description "Allow SSH access"
		```
		
	3. Download the YAML file locally. This will provide instructions on how to setup a Cloud Datalab VM
	
		```
		gsutil cp gs://cloud-datalab/server.yaml ./datalab-server.yaml
		```
		
	4. Create the Datalab VM instance. Make sure to choose an instance name that is unique, and check [here](https://cloud.google.com/compute/docs/regions-zones/regions-zones#choosing_a_region_and_zone) for questions regarding choosing a region/zone for the VM.
	
		```
		gcloud compute instances create [INSTANCE_NAME] \
			--project [PROJECT_ID] \
			--zone [us-east1-b, or us-east1-c, or us-east1-d] \
			--network datalab-network \
			--image-family container-vm \
			--image-project google-containers \
			--metadata-from-file "google-container-manifest=datalab-server.yaml" \
			--machine-type n1-highmem-2 \
			--scopes cloud-platform
		```
		
	5. SSH into the Datalab VM:
	
		- Linux/OS users:
			
			**Keep "USER" as it is below**. Only change `PROJECT_ID`, `previous zone` and `INSTANCE_NAME`.
	
			```
			gcloud compute ssh --quiet \
				--project [PROJECT_ID] \
				--zone [previous zone] \
				--ssh-flag="-N" \
				--ssh-flag="-L" \
				--ssh-flag="localhost:8081:localhost:8080" \
				"${USER}@[INSTANCE_NAME]"
			```
			You can Ctrl(or Cmd)-Z to put this process in the background.
		- Windows users:

			Unfortunatelly it is a bit troublesome. Please read our tutorials [here](google-cloud-tutorial-windows.md).		
	
	6. Now you can access the Cloud Datalab notebook listings at [http://localhost:8081](http://localhost:8081). After you accept the Datalab terms and conditions, you should be redirected to a page that looks like this:

	<img src="https://cloud.google.com/datalab/images/datalab-launch.png" alt="Cloud Datalab Notebook Start Page" width="75%">
	
	7. If you close the SSH connection or shutdown the instance, next time you will need to redo step v and vi above to reconnect.
	
	

* Data transfer
	
	You can upload files to Datalab by clicking on the "Upload" button in the console. To download a notebook or a file,  open the file in the Datalab console and click "Notebook" (for notebook) or "File" (for other types) in the upper-left corner, then click "Download".
	
	<img src="http://i.imgur.com/POUsx97.png" alt="Download" width="75%">

* Program with Jupyter notebooks
	
	If you are new to programming in Jupyter notebooks, please read our [Jupyter notebook tutorial](jupyter-tutorial.md).
	
	
* Instance management	
	
	Any files you create or upload here will be saved on the persistent disk, so you can stop and restart your VM instance without fear of losing data (which you should do if you're not using your instance - **each minute the VM is on costs money**, and you only get one coupon for the entire semester - so if you run out of credits, you're on your own!)

	You can stop, restart, and manage your VM instances in the [Google Compute Engine tab](https://console.cloud.google.com/compute/) as below.

	<img src="http://i.imgur.com/iVeFyhf.png" alt="GKE Home Page" width="75%">
	
	


## Creating a Datalabs Instance with GPU Support

Due to several complications, Datalab currently couldn't provide GPU support at this moment. We envision the issues will be resolved soon and will inform the class when it is available. 

Note that you don't need GPU to finish the three problem sets.
