FROM ubuntu:16.04

WORKDIR /root

# install development tools
RUN apt-get update -y
RUN apt-get install -y wget
RUN apt-get install -y bzip2
RUN apt-get install -y git
RUN apt-get install -y make g++

# install anaconda
RUN wget https://repo.continuum.io/archive/Anaconda3-5.0.1-Linux-x86_64.sh
RUN sh Anaconda3-5.0.1-Linux-x86_64.sh -u

# build as CPU mode
ENV NO_CUDA 1

# install dependent packages
RUN conda install numpy pyyaml mkl setuptools cmake cffi
RUN conda install -c soumith magma-cuda80

# get pytorch's sources
RUN git clone --recursive https://github.com/pytorch/pytorch

# build and install pytorch
RUN cd pytorch && python setup.py install

