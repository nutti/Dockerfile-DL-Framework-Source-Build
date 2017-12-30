FROM ubuntu:16.04

WORKDIR /root

# install development tools
RUN apt-get update -y
RUN apt-get install -y git
RUN apt-get install -y g++
RUN apt-get install -y curl
RUN apt-get install -y python

# install python
RUN apt-get install -y python-numpy python-dev python-pip python-wheel

# install bazel
RUN apt-get install -y openjdk-8-jdk
RUN echo "deb [arch=amd64] http://storage.googleapis.com/bazel-apt stable jdk1.8" | tee /etc/apt/sources.list.d/bazel.list
RUN curl https://bazel.build/bazel-release.pub.gpg | apt-key add -
RUN apt-get update -y
RUN apt-get install -y bazel

# install pip package
RUN git clone https://github.com/tensorflow/tensorflow

RUN cd tensorflow && echo "\n\n\n\n\n\n\n\n\n" | ./configure 
RUN cd tensorflow && bazel build --config=opt //tensorflow/tools/pip_package:build_pip_package
RUN cd tensorflow && bazel-bin/tensorflow/tools/pip_package/build_pip_package /tmp/tensorflow_pkg
RUN cd tensorflow && pip install /tmp/tensorflow_pkg/tensorflow-1.4.0-cp27-cp27mu-linux_x86_64.whl

