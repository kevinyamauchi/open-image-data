# EM analysis tutorial

## Overview
This tutorial shows how to perform and analyze image segmentations in volume Focused Ion Beam Scanning Electron Microscopy (FIBSEM) data. This workshop will take you through the basics of bioimage analysis in Python and [napari](https://www.napari.org). We will be performing some analysis on segmented mitochondria using a combination of [`napari`](https://www.napari.org), [`empanada`](https://empanada.readthedocs.io/en/latest/empanada-napari.html), and [`napari-clusters-plotter`](https://github.com/BiAPoL/napari-clusters-plotter).


## Goals
The aim of this workshop is to provide an introduction to bioimage analysis in Python and `napari`. By the end of the workshop you should be able to
- use napari as an image viewer
- perform interactive analysis with napari in a [jupyter notebook](https://jupyter.org/)
- make use of the [napari plugin ecosystem](https://www.napari-hub.org/)


## Pre-tutorial setup

So that we can best utilize our time together, please do the following before arriving at the tutorial:

1. Install napari and dependencies. Instructions [here](./em_installation.md).
2. Download the notebooks and launch jupyter notebook. Instructions [here](./notebook_setup.md).

## Tutorial instructions

1. Do the introduction to viewing images in napari (`part_0_viewer_intro.ipynb`).
2. Segment and measure mitochondria using the cellpose plugin (`part_1_segment_and_analyze_mitochondria.ipynb`).