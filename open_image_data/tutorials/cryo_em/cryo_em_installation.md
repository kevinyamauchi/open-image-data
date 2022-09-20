# Setting up your python environment

(content:references:cryoem_python_installation)=
## Installing python via mambaforge

In this tutorial, we will install python via mambaforge, a distribution of anaconda python. However, if you already have anaconda, miniconda, mambaforge, or miniforge installed, those will work as well and you can skip to the next section.

````{tab-set}
```{tab-item} Linux
1. In your web browser, navigate to the [miniforge page](https://github.com/conda-forge/miniforge#mambaforge).
2. Scroll down to the "Mambaforge" header of the "Downloads" section. Click the link to download link for `Mambaforge-Linux-x86_64`.
3. Open your terminal application
4. Navigate to the folder you downloaded the installer to (usually this is in your Downloads folder). If the file was downloaded to your Downloads folder, you would enter:

    ```bash
    cd ~/Downloads
    ```   

5. Execute the installer with the command below. You can use your arrow keys to scroll up and down to read the license agreement and enter "yes" if you agree.

    ```bash
    bash Mambaforge-Linux-x86_64.sh
    ```
6. After installation, you will be asked if you would like to initialize your terminal with "conda init". Enter "yes" to initalize your terminal.
7. To verify your installation worked, close your Terminal window and open a new one. You should see `(base)` to the left of your prompt.

    ```{admonition} Don't see (base)?
    You can manually initialize conda by entering the command below and re-opening your terminal application.

    ```bash
    conda init
    
    ```

```

```{tab-item} Mac OS (Intel)
1. In your web browser, navigate to the [miniforge page](https://github.com/conda-forge/miniforge#mambaforge).
2. Scroll down to the "Mambaforge" header of the "Downloads" section. Click the link to download link for `Mambaforge-MacOSX-x86_64`.
3. Open your Terminal (you can search for it in spotlight - `cmd` + `space`)
4. Navigate to the folder you downloaded the installer to (usually this is in your Downloads folder). If the file was downloaded to your Downloads folder, you would enter:

    ```bash
    cd ~/Downloads
    ```
    
5. Execute the installer with the command below.  You can use your arrow keys to scroll up and down to read the license agreement and enter "yes" if you agree.

    ```bash
    bash Mambaforge-MacOSX-x86_64.sh
    ```

6. After installation, you will be asked if you would like to initialize your terminal with "conda init". Enter "yes" to initalize your terminal.   
7. To verify your installation worked, close your Terminal window and open a new one. You should see `(base)` to the left of your prompt.
    
    ```{admonition} Don't see (base)?
    You can manually initialize conda by entering the command below and re-opening your terminal application.

    ```bash
    conda init
    ```

```

```{tab-item} Mac OS (M1/M2)
1. In your web browser, navigate to the [miniforge page](https://github.com/conda-forge/miniforge#mambaforge).
2. Scroll down to the "Mambaforge" header of the "Downloads" section. Click the link to download link for `Mambaforge-MacOSX-arm64`.
3. Open your Terminal (you can search for it in spotlight - `cmd` + `space`)
4. Navigate to the folder you downloaded the installer to (usually this is in your Downloads folder). If the file was downloaded to your Downloads folder, you would enter:

    ```bash
    cd ~/Downloads
    ```
    
5. Execute the installer with the command below. You can use your arrow keys to scroll up and down to read it/agree to it.

    ```bash
    bash Mambaforge-MacOSX-arm64.sh
    ```
    
6. After installation, you will be asked if you would like to initialize your terminal with "conda init". Enter "yes" to initalize your terminal. 
7. To verify your installation worked, close your Terminal window and open a new one. You should see `(base)` to the left of your prompt.

    ```{admonition} Don't see (base)?
    You can manually initialize conda by entering the command below and re-opening your terminal application.

    ```bash
    conda init
    ```

```

```{tab-item} Windows
1. Find the file you downloaded (Mambaforge-Windows-x86_64.exe) and double click to execute it. Follow the instructions to complete the installation.
2. Once the installation has completed, you can verify it was correctly installed by searching for the "mambaforge prompt" in your Start menu.
```
````

## Setting up your environment

```{admonition} Using conda instead of mamba?
The following assumes that you have installed python using Mambaforge as [described above](content:references:cryoem_python_installation). If you are using a pre-existing installation of python via anaconda, miniconda, or miniforge, you can simply replace the `mamba` commands with `conda`.

```

1. Download the environment file. This contains all of the libraries required for the tutorial and we will use it to set up our conda environment. To download, right click and "Save as" [this link](https://github.com/kevinyamauchi/cryoem-napari-tutorial/raw/main/environment.yaml). Take note of the path to where you downloaded the file.
1. Open your terminal.
    - **Linux**: Open your terminal application
    - **Mac OS**: Open Terminal (you can search for it in spotlight - cmd + space)
    - **Windows**: Open the "manbaforge prompt" or "miniforge prompt" from your start menu

2. We use an environment to encapsulate the python tools used for this workshop. This ensures that the requirements for this workshop do not interfere with your other python projects. To create the environment (named `cryoem-napari`) from the environment file you downloaded in the first step, enter the following command. Replace `path/to/environment.yaml` with the path to the `environment.yaml` file you downloaded in the first step. You can also drag and drop the `environment.yaml` file into your terminal window to get the path.

	```bash
	mamba env create -f path/to/environment.yaml
	```

3. Once the environment setup has finished, activate the environment. If you successfully activated the environment, you should now see `(cryoem-napari)` to the left of your command prompt.

	```bash
	mamba activate cryoem-napari
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
