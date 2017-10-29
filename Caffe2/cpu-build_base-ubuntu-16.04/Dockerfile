FROM ubuntu:16.04

WORKDIR /root

RUN apt-get update -y
RUN apt-get install -y --no-install-recommends \
        build-essential \
        cmake \
        git \
        libgoogle-glog-dev \
        libprotobuf-dev \
        protobuf-compiler \
        python-dev \
        python-pip

RUN pip install numpy protobuf
RUN pip install future

RUN git clone --recursive https://github.com/caffe2/caffe2.git
RUN cd caffe2 && make && cd build && make install

ENV PYTHONPATH ${PYTHONPATH}:/usr/local
ENV LD_LIBRARY_PATH ${LD_LIBRARY_PATH}:/usr/local/lib

