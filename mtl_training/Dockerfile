FROM nvcr.io/nvidia/cuda:11.8.0-cudnn8-devel-ubuntu22.04

# Let's start with python 3.10 - supported on jammy 
# issues with back portability for some of the versions can be handled
# Keep a track of them 
# Proceed with PyTorch 1.13 as there are no wheels for pytorch 1.13 with cuda 11.8
# and see if there are no issues
# if issues - install PyTorch 2.0 

# Set up Image and Container Args 
ENV DEBIAN_FRONTEND=noninteractive
ENV WORKSPACE="/workspace/"


# Set up Locales 
RUN apt-get update && apt-get install -y locales 
ENV LANG="en_US.UTF-8" LC_ALL="en_US.UTF-8" LANGUAGE="en_US.UTF-8"
RUN echo "en_US.UTF-8 UTF-8" > /etc/locale.gen && \
    locale-gen --purge $LANG && \
    dpkg-reconfigure --frontend=noninteractive locales && \
    update-locale LANG=$LANG LC_ALL=$LC_ALL LANGUAGE=$LANGUAGE

# Set up TimeZone
ENV TZ=America/Los_Angeles
RUN echo ${TZ} > /etc/timezone


# Set up Required Dependency Binaries from apt package manager 
RUN apt-get update && apt-get install -y \
    curl \
    git \
    nano \
    python3 \ 
    python-is-python3 \
    python3-pip \
    wget \
    && rm -rf /var/lib/apt/lists* \
    && apt-get clean 

# Install required frameworks and tools 
RUN python3 -m pip install -U setuptools pip \
    black \
    coverage \
    cupy-cuda11x \
    flake8 \
    grpcio \
    grpcio-tools \
    isort \
    onnx \
    onnxruntime \
    pytest \
    pytest-grpc \
    tensorboard \
    wandb

# RUN python -m cupyx.tools.install_library --cuda 11.x --library cutensor

# Install the Torch Library 
# RUN python3 -m pip install torch==2.0.0+cu118 torchvision==0.15.1+cu118 --index-url https://download.pytorch.org/whl/cu118 
RUN python3 -m pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118
RUN python3 -m pip install -U xformers 
RUN python3 -m pip install lightning

# Expose the Workdir of the Image 
WORKDIR ${WORKSPACE}
