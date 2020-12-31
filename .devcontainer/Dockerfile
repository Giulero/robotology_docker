# See here for image contents: https://github.com/microsoft/vscode-dev-containers/tree/v0.154.0/containers/ubuntu/.devcontainer/base.Dockerfile

# [Choice] Ubuntu version: bionic, focal
ARG VARIANT="focal"
FROM mcr.microsoft.com/vscode/devcontainers/base:0-${VARIANT}

# [Optional] Uncomment this section to install additional OS packages.
# RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
#     && apt-get -y install --no-install-recommends <your-package-list-here>
RUN apt-get update && \
    apt-get install -y build-essential \
    cmake \
    cmake-curses-gui \
    coinor-libipopt-dev \
    freeglut3-dev \
    git \
    libace-dev \
    libboost-filesystem-dev \
    libboost-system-dev \
    libboost-thread-dev \
    libdc1394-22-dev \
    libedit-dev \
    libeigen3-dev \
    libgsl0-dev \
    libjpeg-dev \
    liblua5.1-dev \
    libode-dev \
    libopencv-dev \
    libsdl1.2-dev \
    libtinyxml-dev \
    libv4l-dev \
    libxml2-dev \
    lua5.1 \
    portaudio19-dev \
    python3-dev python3-numpy \
    qml-module-qt-labs-folderlistmodel \
    qml-module-qt-labs-settings \
    qml-module-qtmultimedia \
    qml-module-qtquick-controls \
    qml-module-qtquick-dialogs \
    qml-module-qtquick-window2 \
    qml-module-qtquick2 \
    qtbase5-dev \
    qtdeclarative5-dev \
    qtmultimedia5-dev \
    swig \
    libmatio-dev

# Get gazebo
ARG GAZEBO_VER=9

RUN apt-get install -y gazebo${GAZEBO_VER} &&\
    apt-get install -y libgazebo${GAZEBO_VER}-dev

ENV Robotology_DIR=/iit

RUN mkdir -p ${Robotology_DIR} &&\
    cd ${Robotology_DIR} &&\
    git clone https://github.com/robotology/robotology-superbuild.git

ARG USERNAME
ARG USEREMAIL
RUN git config --global user.name USERNAME
RUN git config --global user.email USEREMAIL

RUN cd ${Robotology_DIR}/robotology-superbuild &&\
    mkdir -p build && cd build &&\
    cmake \
          -DROBOTOLOGY_ENABLE_CORE:BOOL=ON \
          -DROBOTOLOGY_ENABLE_DYNAMICS:BOOL=ON \
          -DROBOTOLOGY_USES_GAZEBO:BOOL=ON \
          -DROBOTOLOGY_USES_OCTAVE:BOOL=OFF \
          -DROBOTOLOGY_USES_PYTHON:BOOL=ON \
          -DROBOTOLOGY_USES_MATLAB:BOOL=OFF \
          .. && make &&\
    echo "source ${Robotology_DIR}/robotology-superbuild/build/install/share/robotology-superbuild/setup.sh" >> /etc/bash.bashrc


CMD ["bash"]
