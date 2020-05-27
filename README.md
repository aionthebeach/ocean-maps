# Analysing Fishing vessel data and their relation with the animals such as Sharks

## Installation

**This repo was originally built using Arch Linux and as such has some Linux-specific dependencies, however, we have gotten the project to run on both Linux and Windows using WSL**

More information here on WSL:
https://docs.microsoft.com/en-us/windows/wsl/about

## Getting started on Windows
**GPU support coming but not yet available until Windows releases a version supporting it**

1. Follow the Microsoft document listed below. Be sure to upgrade to WSL 2. This requires becoming a Windows Insider, which is a simple sign-up process. You may need to restart a few times, as per instructions.

**Please install Ubuntu as the Linux distro of choice.**

    https://docs.microsoft.com/en-us/windows/wsl/install-win10

2. Once Ubuntu is installed **do not use command prompt or Powershell to run it, hit the Windows key and search for the Ubuntu terminal directly.** 

3. When you're in Ubuntu, download Anaconda by entering the following into the terminal:

        wget  https://repo.anaconda.com/archive/Anaconda3-2019.03-Linux-x86_64.sh

4. Then install it via the following command:

        bash Anaconda3-2019.03-Linux-x86_64.sh

5. Follow through the prompts on the sceen to install Anaconda

6. Once Anaconda is installed, navigate to the folder on Windows where your repository is within the terminal. **Linux uses a different syntax in which the user must prepend "/mnt/<driveletter> to the drive** Make sure you go into the notebook folder and not the parent folder. Example code below:

        cd /mnt/c/projects/AIoTB/notebook/

6. Run the following command to create the environment:

        conda env create -f environment.yml

7. It will take a while to download the requisite packages. Once it's finished activate the environment with this command:

        conda activate aionthebeach

8. We're ready to run the notebook now, so enter in the below:

        conda activate aionthebeach

**You will receive an error that looks like**

        This command cannot be run due to the error: The system cannot find the file specified.

This is fine, just copy and paste one of the HTTP links below into your browser. Example:

    http://localhost:8888/?token=8883967c381b6a5b72a744dd1633d8a4b9f6abed8a55cfe1

Voila, you now have AIoTB running on your Windows machine!

## Getting started on Linux
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
