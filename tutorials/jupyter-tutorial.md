---
layout: page
title: Jupyter Tutorial
permalink: /tutorials/jupyter-tutorial/
---

In this class, we will use [Jupyter notebooks](https://jupyter.org/) for the assignments. Jupyter notebooks provide an web browser-based programming enviroment where you can execude code in blocks, display the output figure, and annotate in Markdown *in situ*. With these properties, it's been widely used in the scientific community to make research project reproducible.

## Set up a Jupyter server

A jupyter server is a hub that can host many notebook instances.

### On Google Cloud

Please refer to the official [Google Cloud tutorial](https://cloud.google.com/datalab/docs/quickstart).

### On your local machine

First you should install jupyter by:

```bash
pip install jupyter
```
In the conda enviroment we provide for the assignments, jupyter has already been installed. 
Follow the below steps (here we take pset 1 as an example) to activate the environment:


- Install conda following instructions [here](https://github.com/mit6874/mit6874.github.io/blob/master/tutorials/conda-tutorial.md).
- Create a conda environment using the provided yaml file (e.g, pset1_env.yml)
	
	```
	cd DIR_OF_PSET1
	conda env create -f pset1_env.yml
	```
- Activate the provided conda environment
	
	```bash
	source activate pset1
	```

Then start the Jupyter server by:

```bash
jupyter notebook
```

This will automatically open a browser tab. If not, manually open a new webpage at http://localhost:8888 . You will be able to see the main console of the server as below:

<div class='fig figcenter'>
  <img src='/assets/jupyter/browser.png'>
</div>

Note that you can only access the sub-directories of the folder where you ran `jupyter notebook`. So make sure you start the server outside of the folder that you put data and notebooks.

## Start a new notebook
Navigate to the folder that you want to create a notebook in. Click on "New" on the right side of the console and the select "Python 3"

## Program in notebook
There are many detailed tutorials online. Here we provide some pointers to tutorials and examples that you might find useful:

- [Video tutorial](https://www.youtube.com/watch?v=HW29067qVWk)
- [Examples of notebooks](https://github.com/jdwittenauer/ipython-notebooks).

## Tips
- Always remember to save the notebook when you exit.
- You will NOT lose your **variables** if you simply save and close the tab. But you WILL lose them if you either "shutdown" a notebook as illustrated in the figure below or you shutdown the jupyter server. However, in either case, all the **code** will still be there as long as you've saved.

<div class='fig figcenter'>
  <img src='/assets/jupyter/shutdown.png'>
</div>





