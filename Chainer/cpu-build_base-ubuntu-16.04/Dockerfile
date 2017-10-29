FROM ubuntu:16.04

WORKDIR /root

# install development packages
RUN apt-get update -y
RUN apt-get install -y python
RUN apt-get install -y wget
RUN apt-get install -y git

# install pip
RUN wget https://bootstrap.pypa.io/get-pip.py
RUN python get-pip.py

# install dependent modules
RUN pip install -U setuptools
RUN pip install numpy six

# get chainer's sources
RUN git clone https://github.com/chainer/chainer.git

# build and install chainer
RUN cd chainer && python setup.py install

