# Setup

## Getting the code
- Option 1: if you're comfortable with Github, fork [the repository](https://github.com/ktcarr/whoi-climate-data-tutorial/) (see [this page](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo) for more on forking), then clone it to your PC.
- Option 2: Download the repository as a .zip file: go to [the repository home page](https://github.com/ktcarr/whoi-climate-data-tutorial/), then click "Code -> Download ZIP".

## Virtual environment
1. Set up mamba or conda (if not already). To set up, download and install miniforge following the instructions here: https://github.com/conda-forge/miniforge.
2. Navigate to the project home folder (e.g., with ```cd ~/whoi-climate-data-tutorial```)
3. Create a conda/mamba environment for the project with: ```mamba create -p ./envs``` and activate the environment with ```conda activate ./envs```
4. Next, install necessary packages in the environment with:<sup>3,4</sup>
    - ```mamba env update -p ./envs --file environment.yml``` 
5. Install custom module (```src```) in the environment with ```pip install -e .```

<sup>4</sup>If you're using conda and the ```conda install ...``` / ```conda env update ...``` commands are taking a long time, you could try [updating the solver to "libmamba"](https://www.anaconda.com/blog/a-faster-conda-for-a-growing-community). If this doesn't work, you could also try setting the channel priority to flexible, with ```conda config --set channel_priority flexible``` (thanks to Lilli Enders for suggesting this).

## Running the code (locally)
1. Navigate to project folder
2. Activate virtual environment (```conda activate ./envs```)
3. Start jupyter lab with by typing ```jupyter lab``` in terminal / command window

## Accessing the climate data servers
Note: to access the data, you must be on the WHOI network (i.e., on the WHOI wifi or connected by VPN).

### Option 1 (preferred): mounting the network file system
- Windows and (non-Mac) Linux users: follow [online instructions for CMIP5](http://cmip5.whoi.edu/?page_id=40) or [for CMIP6](http://cmip6.whoi.edu/?page_id=50).
- Mac users: for CMIP6, open Finder, then select "Go" from the top menu bar and click "Connect to Server". Then, enter ```smb://vast.whoi.edu/proj/cmip6```. If prompted, enter your WHOI username (*without* "@whoi.edu") and password. Note the default mount location for the server is ```/Volumes/data```. For CMIP5, use the same process but with the following server address: ```smb://cmip5.whoi.edu```.

#### Option 2: downloading the data and running locally
**For reanalysis and model data used in the tutorial**:
- Download data from the [shared Google Drive folder](https://drive.google.com/drive/folders/1V-aHzoYYUrU6d5ExnxEORiZxeAAisx_e?usp=drive_link)

**For other (CMIP6) model output**:
- Go to [http://cmip6.whoi.edu/search](http://cmip6.whoi.edu/search).
- Click on the the "HTTP" link in the "Files" column for a dataset you'd like to download.
- On the next page, select individual files to download.
- (optional) Save these files to a folder called ```data``` in this project.

#### Option 3: running in the cloud
- Go to [https://colab.research.google.com/](https://colab.research.google.com/)
- In Google Colab, click "File -> Open notebook -> Upload" and select one of the tutorial notebooks. 
- Go to the [shared Google Drive folder](https://drive.google.com/drive/folders/1V-aHzoYYUrU6d5ExnxEORiZxeAAisx_e?usp=drive_link)
- Click the three dots next to the "climate-data" folder and click "Organize -> Add shortcut", then select "My Drive"
- Note: **if using Google Colab, the regridding components of the tutorial will not work**, owing to package compatibility issues (cannot import the ```xesmf``` package in Colab, possibly related to [this issue](https://github.com/conda-forge/esmf-feedstock/issues/91)).


