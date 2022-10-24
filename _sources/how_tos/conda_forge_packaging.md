# Making your package available on conda-forge

## Overview

This how-to teaches how to make your pypi installable with conda via `conda-forge`.

**Prerequisites**

- You have a package available on pypi that you want to make available on 
- You have a github account
- You know how to clone and push repositories with git
- You have conda installed on your computer


**Related reading**

- [conda-forge contributing packages docs](https://conda-forge.org/docs/maintainer/adding_pkgs.html)
- [Blog post on grayskull](https://conda-forge.org/blog/posts/2020-03-05-grayskull/)


## Instructions


1. Fork the conda-forge `staged-recipes` library. Forking is the process of making a copy of a repository in your own account. We will make our new recipe to build our package on conda in this repository. We fork the repository instead of making the changes directly on the official `conda-forge` recipe to avoid cluttering the official repository.

	1. Log into your github account.
	2. Navigate your web browser to the [`staged-recipes` repository](https://github.com/conda-forge/staged-recipes).
	3. Click the "fork" button to begin the forking process.

	```{image} ./resources/conda_forge_packaging/fork_staged_recipes.png
	:alt: fork the staged-recipes repository
	:width: 600
	:align: center
	```
	
	4. Click the green "Create fork" button to confirm your fork.

		```{image} ./resources/conda_forge_packaging/confirm_fork.png
		:alt: confirm fork creation
		:width: 600
		:align: center
		```
	
	5. When the fork is completed, you will be taken to your fork. Note that the repository is now in your github account and it says it is "forked from `conda-forge/staged-recipes`". 
		
		```{image} ./resources/conda_forge_packaging/fork_completed.png
		:alt: confirm fork creation
		:width: 600
		:align: center
		```
	

2. Clone your fork of the `staged-recipes` to your computer. Click the green "Code" button on the repository and copy the `git@...` address. Then use the `git clone` command to clone the repository to the directory of your choosing.

	```{image} ./resources/conda_forge_packaging/clone_repo_link.png
	:alt: confirm fork creation
	:width: 600
	:align: center
	```

	```bash
	git clone <repo git address>
	```

3. Create a conda environment to install `grayskull`, the utility for generating your conda build recipe. In your terminal, create a new environment called "grayskull"

	 ```bash
	 conda create -n grayskull
	 ```
 
2. After the environment creation finishes, activate your new "grayskull" environment.
	
	```bash
	conda activate grayskull
	```
 	
3. Install `grayskull` from the `conda-forge` channel.
 	
 	```bash
 	conda install -c conda-forge grayskull
	```
 	
4. Navigate to the `recipes` directory of your `staged-recipes` fork that you cloned.
 
 	```bash
 	cd path/to/staged-recipes/recipes
 	```
	 
5. 	Use grayskull to generate the recipe from your pypi python  package. Enter the command below in your terminal, replacing `<pypi package name>` with the name of your package (i.e., the name you use when you do `pip install <pypi package name>`).

	```bash
	 grayskull pypi --strict-conda-forge <pypi package name>
 	```

6. Upon completion, a folder with the name of your package will be generated. Within that folder, there will be a `meta.yaml` file containing your conda recipe. For more information on the `meta.yaml` file, see the [`conda-build` docs](https://docs.conda.io/projects/conda-build/en/latest/resources/define-metadata.html). As an example, see the `meta.yaml` from [napari-threedee](https://github.com/napari-threedee/napari-threedee) below

	```{toggle}
	
		{% set name = "napari-threedee" %}
		{% set version = "0.0.1" %}
		
		package:
		  name: {{ name|lower }}
		  version: {{ version }}
		
		source:
		  url: https://pypi.io/packages/source/{{ name[0] }}/{{ name }}/napari-threedee-{{ version }}.tar.gz
		  sha256: 7b468a891d5581f3c2446cfd05a58d62812e817aaa2b01b73f242449126ea5fd
		
		build:
		  noarch: python
		  script: {{ PYTHON }} -m pip install . -vv
		  number: 0
		
		requirements:
		  host:
		    - python >=3.8
		    - setuptools-scm
		    - pip
		  run:
		    - python >=3.8
		    - npe2
		    - napari
		    - numpy
		    - qtpy
		
		test:
		  imports:
		    - napari_threedee
		  commands:
		    - pip check
		  requires:
		    - pip
		
		about:
		  home: https://github.com/alisterburt/napari-threedee
		  summary: A suite of useful tools based on 3D interactivity in napari
		  license: BSD-3-Clause
		  license_file: LICENSE
		
		extra:
		  recipe-maintainers:
		    - kevinyamauchi
		    - alisterburt
		
		
	```

7. If you are satisfied with the recipe (generally this works for packages with out complicated-to-install dependencies (e.g., pytorch), you can now commit the change. The instructions below are assuming the package name is `napari-threedee`. Replace `napari-threedee` with the name of your package.

	```bash
	# create a new branch
	git checkout -b add-napari-threedee
	
	# add the meta.yaml file
	git add napari-threedee/meta.yaml
	
	# commit the new file
	git commit -m "add the recipe for napari-threedee"
	
	# push the changes (change add-napari-threedee to your branch name)
	git push --set-upstream origin add-napari-threedee
	
	```

8. Now you will create a pull request on the conda-forge/staged-recipes repo so that your new recipe can be reviewed. Navigate to the [`conda-forge/staged-recipes`](https://github.com/conda-forge/staged-recipes) repo with your web browser. Since you just pushed a new branch to your fork, you should see a button to open a new pull request. Open the pull request once you have read the instructions in the template.
9. The pull request will perform automatic tests. You can view them at the bottom of your pull request (screenshot below). Once they have all passed (all green checkmarks), you can request review from the team by making a comment on your pull request with the following message: `This is ready for review @conda-forge-admin, please ping team`
10. The `conda-forge` team will then review your new recipe. Once they approve, you are done! Congratulations!

