FROM pytorch/pytorch:1.1.0-cuda10.0-cudnn7.5-runtime
MAINTAINER Sergi Valverde <svalverde@eia.udg.edu>


# --------------------------------------------------
# User management
# - docker user
# --------------------------------------------------
RUN useradd -ms /bin/bash docker
ENV HOME /home/docker
USER root

# --------------------------------------------------
# packages to install. See readme for a list of
# included packages
# --------------------------------------------------
ADD requirements.txt /requirements.txt
RUN pip install pip --upgrade
RUN pip install -r /requirements.txt


# --------------------------------------------------
# data structure
# - shared folders between the docker and host: /data
# - source files inside the docker: $HOME/src
# - dummy files for testing: $HOME/dummy
# --------------------------------------------------
RUN mkdir /data
RUN mkdir $HOME/src
RUN mkdir $HOME/dummy
ENV PATH=/$HOME/src:${PATH}
ADD dummy/T1.nii.gz $HOME/dummy/T1.nii.gz

USER docker
WORKDIR $HOME/src
