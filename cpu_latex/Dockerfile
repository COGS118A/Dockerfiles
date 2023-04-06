# 1) choose base container
# generally use the most recent tag

# base notebook, contains Jupyter and relevant tools
# See https://github.com/ucsd-ets/datahub-docker-stack/wiki/Stable-Tag 
# for a list of the most current containers we maintain


ARG BASE_CONTAINER=ucsdets/datascience-notebook:2023.2-stable

FROM $BASE_CONTAINER

LABEL maintainer="UC San Diego ITS/ETS <ets-consult@ucsd.edu>"

# 2) change to root to install packages
USER root

RUN apt-get -y install htop

RUN apt-get update
RUN apt-get -y install pandoc texlive-xetex texlive-fonts-recommended texlive-plain-generic build-essential libcurl4-gnutls-dev libxml2-dev libssl-dev libgit2-dev texlive-lang-chinese

# 3) install packages using notebook user
USER jovyan

# RUN conda install -y scikit-learn

RUN pip install --upgrade pip
RUN pip install --no-cache-dir networkx scipy
# reinstall

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

RUN conda 

# Override command to disable running jupyter notebook at launch
# CMD ["/bin/bash"]