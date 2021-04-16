# See here for image contents: https://github.com/microsoft/vscode-dev-containers/tree/v0.166.1/containers/ubuntu/.devcontainer/base.Dockerfile

# [Choice] Ubuntu version: bionic, focal
ARG VARIANT="focal"
FROM mcr.microsoft.com/vscode/devcontainers/base:0-${VARIANT}

# [Optional] Uncomment this section to install additional OS packages.
# RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
#     && apt-get -y install --no-install-recommends <your-package-list-here>


RUN apt-get update -y
RUN apt-get install -y build-essential libasound2-dev wget git
RUN git clone https://github.com/pjsip/pjproject.git
RUN cd pjproject && \
    export CFLAGS="$CFLAGS -fPIC" && \
    ./configure --enable-shared && \
    make dep && \
    make && \
    make install

RUN apt-get install -y build-essential libasound2-dev wget git python3-dev python3-pip

RUN cd /pjproject/pjsip-apps/src/ && \
    git clone https://github.com/mgwilliams/python3-pjsip.git && \
    cd python3-pjsip && \
    python3 setup.py build && \
    python3 setup.py install

RUN ldconfig /usr/local/lib

RUN ls -lh