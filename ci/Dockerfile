FROM pangeo/base-image:2021.09.30
# build file for pangeo images

# FIXME (?): user and home folder is hardcoded for now
# FIXME (?): this line breaks the cache of all steps below
COPY --chown=jovyan:jovyan . /home/jovyan/.kernels

USER root

RUN wget -O quarto.deb https://github.com/quarto-dev/quarto-cli/releases/download/v0.2.360/quarto-0.2.360-linux-amd64.deb && dpkg -i quarto.deb

USER ${NB_USER}

RUN conda init zsh && conda init bash

WORKDIR ${HOME}/.kernels
RUN chmod +x install-kernels.sh && cd /home/jovyan/.kernels && ./install-kernels.sh environments







