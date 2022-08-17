FROM tensorflow/tensorflow:2.7.3-gpu-jupyter

LABEL maintainer="ko.sugawara@ens-lyon.fr"

ARG NVIDIA_DRIVER_VERSION=455

RUN apt-get update && apt-get install -y --no-install-recommends \
    ocl-icd-dev \
    ocl-icd-opencl-dev \
    opencl-headers \
    clinfo \
    libnvidia-compute-${NVIDIA_DRIVER_VERSION} \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

RUN python3 -m pip install --upgrade pip
RUN python3 -m pip install gputools edt imagecodecs natsort
COPY . /src
RUN python3 -m pip install /src && rm -rf /src