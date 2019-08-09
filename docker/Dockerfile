FROM jupyter/datascience-notebook:58169ec3cfd3
COPY requirements.txt /tmp/
# HACK: set the PROJ_LIB env variable that's required by basemap
ENV PROJ_LIB $CONDA_DIR/share/proj/
RUN conda install --debug --yes --file /tmp/requirements.txt && \
    fix-permissions $CONDA_DIR && \
    fix-permissions /home/$NB_USER

RUN jupyter labextension install jupyterlab_vim
