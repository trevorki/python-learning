# python-learning
This is meant to help people get 

## Setup your software stack
This is a long and sometimes painful step but it's absolutely vital to to any real work using Python. The UBC Masters of Data Science has an excellent and comprehensive installation guide [__here__](https://ubc-mds.github.io/resources_pages/installation_instructions/). 

Select your operating system then follow the steps for the following sections and ignore the others.

- **Visual Studio Code**
- **GitHub**: ignore the UBC MDS organization stuff
- **Git, Bash, and Windows Terminal**
- **Python, Conda, and JupyterLab**: Do not install otter-grader
- **VS Code extensions**: Ignore the Quarto extension
- **Improving the bash configuration**

## Create a virtual environment
This is important because sometimes library A needs library X version 1.2, but library B needs library X version 1.3. So if you update to verision 1.3, then library A won't work. It's a problem the is solved by **virtual environments**.

We Will be using the conda environment manager to create virtual environments. To create a virtual environment you can follow these steps:

#### Managing environments through terminal commands
- create an empty environment with the desired python version
    ```bash
    conda create --name my_env python=3.12
    ```
- activate it
    ```bash
    conda activate my_env
    ```
- add packages to it (eg `pandas`, `matplotlib`)
    ```bash
    conda install pandas matplotlib
    # or specify the versions
    conda install pandas=2.2.2 matplotlib>3.8
    ```
- you can also use `pip` to install packages into 
the currently active conda environment. This is useful because not all packages are available through conda channels.

#### Mangaing environments using environment files
You can also use a `environment.yml` or `requirements.txt`. Here is the `environment.yml` file used to create the environment used to run code from this repo. Note that you don't have to specify version numbers, but it is generally a good practice so that future package updates won't break your code.

```yaml
name: 'py'
channels:
  - conda-forge
dependencies:
  - python = 3.12
  - pip
  
  # Conda packages
  - ipykernel # for use with Jupyter
  - pandas=1.26.4
  - numpy=2.2.2
  - plotly=5.22.0
  
  ## PyPI packages
  - pip: 
    - python-dotenv==1.0.1
    - scipy==1.12
    - nbformat==5.10.4
    - matplotlib==3.9.0
    - ipywidgets==8.1.3
```
From the directory containing the file, enter the following line to create and install all the packages as specified in the file. Easy!
```bash
conda env create --file environment.yml
```
See [Conda Cheat Sheet](https://docs.conda.io/projects/conda/en/4.6.0/_downloads/52a95608c49671267e40c689e0bc00ca/conda-cheatsheet.pdf) for reference.


## Jupyter Lab
Is an program that runs in a browser, allowing you to write code in *Jupyter Notebooks* which are a convenient way write and evaluate code one chunk at a time. Launch jupyte lab from the terminal with

```bash
jupyter lab
```

This should open a new browser tab with Jupyter lab running. From there you should be able to open a notebook file and be under way. Start with  `1-jupyter-notebooks.ipynb` and work your way through the rest of the notebooks.

To shut down jupyter lab, either select File>Shut Down or go back to the terminal and enter CTRL-C-C (hit c twice).

Have fun!

