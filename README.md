# Analysing Fishing vessel data and their relation with the animals such as Sharks

## Installation
### Installing Conda
- Follow instructions to install [Anaconda](https://docs.anaconda.com/anaconda/install/) for Python 3.6+

### Creating Virtual Environment
- conda env create -f environment.yml
- conda activate aionthebeach

### Running with docker
We also have a docker image you can run rather than installing dependencies
manually with conda. The image is hosted (publically, so don't add any private
data for the time being) on [docker hub](https://hub.docker.com/r/aionthebeach/data-science). To start jupyter lab with access to the notebooks in this repo, run the following command from the root dir of this repo:

`$ docker run -p 8888:8888  -e JUPYTER_ENABLE_LAB=yes -v $(pwd):/home/jovyan/work aionthebeach/data-science:latest`

Additional supported options
[here](https://jupyter-docker-stacks.readthedocs.io/en/latest/using/common.html).
The kepler plugin is broken in jupyter lab so to run jupyter notebook instead
just remove `-e JUPYTER_LAB_ENABLE=yes`. To get a shell in your running
container, `docker ps` will give you a container id and `docker exec -it
<containerid> bash` will give you a bash shell.

#### Updating docker image
If you need to modify the docker image (for example to add dependencies) you
can build a new image tagged with your latest git commit and push it up to the
AI On The Beach repo on dockerhub.

`$ docker build --tag=data-science:$(git rev-list HEAD --abbrev-commit | head -n1) ./docker/.`

`$ docker tag data-science:$(git rev-list HEAD --abbrev-commit | head -n1) aionthebeach/data-science`

`$ docker push aionthebeach/data-science:latest`

If you haven't been added to the AI on the beach docker repo the docker push will fail, contact Zach WF to get access.
