FROM jupyter/datascience-notebook:58169ec3cfd3
COPY requirements.txt /tmp/

# HACK: set the PROJ_LIB env variable that's required by basemap
ENV PROJ_LIB $CONDA_DIR/share/proj/
RUN conda install --yes --file /tmp/requirements.txt && \
    fix-permissions $CONDA_DIR && \
    fix-permissions /home/$NB_USER
# Install dependencies not available through conda through pip
RUN pip install keplergl==0.1.0a8

RUN jupyter labextension install jupyterlab_vim
RUN jupyter nbextension install --py --sys-prefix keplergl
RUN jupyter nbextension enable --py --sys-prefix keplergl
