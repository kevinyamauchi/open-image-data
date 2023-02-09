# Introduction to napari plugins

## Overview
This workshop will take you through the basics of bioimage analysis in Python and [napari](https://www.napari.org) and developing napari plugins. In the first part, we will be performing some analysis of fluorescently-labeled nuclei with [`napari`](https://www.napari.org), [`stardist`](https://github.com/stardist/stardist), and [`napari-clusters-plotter`](https://github.com/BiAPoL/napari-clusters-plotter). In the second part, we will make your first napari plugin.


## Goals
The aim of this workshop is to provide an introduction to bioimage analysis in Python and `napari`. By the end of the workshop you should be able to
- use napari as an image viewer
- perform interactive analysis with napari in a [jupyter notebook](https://jupyter.org/)
- make use of the [napari plugin ecosystem](https://www.napari-hub.org/)
- make a simple napari plugin


## Pre-tutorial setup

So that we can best utilize our time together, please do the following before arriving at the tutorial:

1. Install napari and dependencies. Instructions [here](./napari_plugin_installation.md).
2. Download the notebooks. Instructions [here](./napari_plugin_notebook_setup.md).

## Tutorial instructions

1. Do the introduction to viewing images in napari (`part_0_viewer_intro.ipynb`).
3. Segment and measure nuclei using the stardist and napari-clusters-plotter plugins  (`part_1_segmenting_and_measuring_nuclei.ipynb`).
4. Perform spot detection using your own spot detection function. There are 3 versions of this tutorial (see description below). They all cover the same content, they just require more or less coding depending on experience level.
    - `part_2_spot_detection_tutorial_beginner.ipynb`: this is the activity notebook for people new to image processing with python
    - `part_2_spot_detection_tutorial_advanced.ipynb`: this is the activity notebook for people with experience performing image processing with python
    - `part_2_spot_detection_tutorial_solution.ipynb`: this is the solution to the activity.
5. Turn your spot detection function into a napari plugin. Instructions [here](./make_a_simple_plugin.md).
6. Extend your plugin (ideas here) or make your own napari plugin.