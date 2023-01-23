# Setting up your python environment

(content:references:napari_python_installation)=
## Installing python via mambaforge

In this tutorial, we will install python via mambaforge, a distribution of anaconda python. However, if you already have anaconda, miniconda, mambaforge, or miniforge installed, those will work as well and you can skip to the next section.

To install python via mambaforge, follow the instructions [here](../../how_tos/install_python).

## Setting up your environment

```{admonition} Using conda instead of mamba?
The following assumes that you have installed python using Mambaforge as [described above](content:references:napari_python_installation). If you are using a pre-existing installation of python via anaconda, miniconda, or miniforge, you can simply replace the `mamba` commands with `conda`.

```

1. Open your terminal.
    - **Linux**: Open your terminal application
    - **Mac OS**: Open Terminal (you can search for it in spotlight - cmd + space)
    - **Windows**: Open the "mambaforge prompt" or "miniforge prompt" from your start menu

2. We use an environment to encapsulate the python tools used for this workshop. This ensures that the requirements for this workshop do not interfere with your other python projects. To create the environment (named `napari-tutorial`), run the command below.

	```bash
	mamba env create -f https://raw.githubusercontent.com/kevinyamauchi/eth-napari-workshop/main/environment.yaml
	```

3. Once the environment setup has finished, activate the environment. If you successfully activated the environment, you should now see `(napari-tutorial)` to the left of your command prompt.

	```bash
	mamba activate napari-tutorial
	```

5. If you are on a Mac or linux, please install these additional dependencies.
    ````{tab-set}
    ```{tab-item} Linux

	```python
	mamba install -c conda-forge ocl-icd-system
	```

    ```{tab-item} Mac OS
	```python
	mamba install -c conda-forge python.app ocl_icd_wrapper_apple
	```

    ````

6. Test that your notebook installation is working. We will be using notebook for interactive analysis. Enter the command below and it should launch jupyter notebook book in a web browser. Once you've confirmed it launches, close the web browser and press ctrl+c in the terminal window to stop the notebook server.

	```bash
	jupyter notebook
	```

7. Test your napari installation. Enter the command below and an empty napari viewer should open. You can close the window after it opens. Please note that it takes a bit of extra time to launch napari the first time.
	
	```bash
	napari
	```

````{admonition} Errors launching?
If you receive an error when attempting to launch and/or install napari, you can ask for help on:
- [image.sc](https://forum.image.sc/): forum for bioimage analysis questions
- [napari zulip](https://napari.zulipchat.com/): chat about napari

````
