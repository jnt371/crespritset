ARG UBUNTU_VER="18.04"
ARG CUDA_VER="10.2"
ARG CUDNN_VER="7"
FROM nvidia/cuda:${CUDA_VER}-cudnn${CUDNN_VER}-devel-ubuntu${UBUNTU_VER}

ARG UBUNTU_VER
ARG CUDA_VER
ARG CUDNN_VER
ARG PYTHON_VER="3.8"
ARG USER_NAME="edith"
ARG PW="0000"
ARG CONDA_PATH=/home/$USER_NAME/miniconda

ENV DEBIAN_FRONTEND=noninteractive
ENV LIBRARY_PATH=$CONDA_PATH/lib:/usr/local/cuda/lib64:/usr/local/cuda/lib64/st$
ENV LD_LIBRARY_PATH=$CONDA_PATH/lib:/usr/local/cuda/lib64:/usr/local/cuda/lib64$
ENV PKG_CONFIG_PATH=$PKG_CONFIG_PATH:$CONDA_PATH/lib/pkgconfig

RUN \
  apt-get update -qq && \
  apt-get install -qq -y \
    git \
    python3 \
    python3-pip \
    python3-matplotlib \
    python3-pyqt5 \
    && rm -rf /var/lib/apt/lists/*

RUN python3 -m pip install -U pip setuptools wheel

RUN python3 -m pip install -v git+https://github.com/wkentaro/labelme.git

RUN mkdir /root/workdir

ENV LANG en-US

WORKDIR /root/workdir
ENTRYPOINT [ "labelme" ]
