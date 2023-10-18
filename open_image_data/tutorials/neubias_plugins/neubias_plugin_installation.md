# Setting up your python environment

**Note:** If you have any issues with installation, please feel free to write us a message on the [napari zulip](https://napari.zulipchat.com/#narrow/stream/212875-general) and we will try to help you get unstuck.

## Installing python via mambaforge

In this tutorial, we will install python via mambaforge, a distribution of anaconda python. However, if you already have anaconda, miniconda, mambaforge, or miniforge installed, those will work as well and you can skip to the next section.

To install python via mambaforge, follow the instructions [here](../../how_tos/install_python).


## Setting up your environment

```{admonition} Using conda instead of mamba?
The following assumes that you have installed python using Mambaforge as [described above](content:references:napari_python_installation). If you are using a pre-existing installation of python via anaconda, miniconda, or miniforge, you can simply replace the `mamba` commands with `conda`.

```

1. Open your terminal.
	- **Windows**: Open the "miniforge prompt" from your start menu
	- **Mac OS**: Open Terminal (you can search for it in spotlight - cmd + space)
	- **Linux**: Open your terminal application
2. We use an environment to encapsulate the python tools used for this workshop. This ensures that the requirements for this workshop do not interfere with your other python projects. To create the environment (named `napari-tutorial`), enter the following command.

	```bash
	mamba create -n napari-tutorial python=3.9
	```

3. Once the environment setup has finished, activate the environment. If you successfully activated the environment, you should now see `(napari-tutorial)` to the left of your command prompt.

	```bash
	mamba activate napari-tutorial
	```

4. Install the dependencies with the commands below

	**If you're on an M1/2 Mac**:

	```bash
	mamba install -c conda-forge notebook napari pyqt
	pip install cookiecutter magicgui
	```

	Other systems: 

	```bash
	mamba install -c conda-forge notebook
	pip install cookiecutter magicgui "napari[all]"
	```

5. If you are on a Mac, please install this one additional dependency.

	```python
	mamba install -c conda-forge python.app
	```

6. Test that your notebook installation is working. We will be using notebook for interactive analysis. Enter the command below and it should launch jupyter notebook book in a web browser. Once you've confirmed it launches, close the web browser and press ctrl+c in the terminal window to stop the notebook server.

	```bash
	jupyter notebook
	```

7. Test your napari installation. Enter the command below and an empty napari viewer should open. You can close the window after it opens. Please note that it takes a bit of extra time to launch napari the first time.
	
	```bash
	napari
	```