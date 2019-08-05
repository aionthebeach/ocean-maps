# Analysing Fishing vessel data and their relation with the animals such as Sharks

## Installation
### System Requirements
- RAM?
- 
### Installing Conda
- Follow instructions to install anaconda

### Creating Virtual Environment
- conda env create -f environment.yml
- conda activate <environmentname>

### Running with docker
We also have a docker image you can run rather than installing dependencies
manually with conda. The image is hosted (publically, so don't add any private
data for the time being) on [docker hub](https://hub.docker.com/r/aionthebeach/data-science). To start jupyter lab with access to the notebooks in this repo, run the following command from the root dir of this repo:

`$ docker run -p 8888:8888  -e JUPYTER_ENABLE_LAB=yes -v $(pwd):/home/jovyan/work aionthebeach/data-science:latest`

Additional supported options [here](https://jupyter-docker-stacks.readthedocs.io/en/latest/using/common.html).

## Running the Analysis

## Observations and Results
