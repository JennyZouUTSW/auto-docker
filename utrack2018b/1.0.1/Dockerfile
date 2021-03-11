# Download and install Matlab Compiler Runtime v9.5 (2018b)
#
# This docker file will configure an environment into which the Matlab compiler
# runtime will be installed and in which stand-alone matlab routines (such as
# those created with Matlab's deploytool) can be executed.
#
# See http://www.mathworks.com/products/compiler/mcr/ for more info.

FROM ubuntu:xenial

# Install the MCR dependencies and some things we'll need and download the MCR
# from Mathworks -silently install it
RUN apt-get -qq update; \
    apt-get -qq install -y unzip xorg wget curl x11-apps; \
    mkdir -p /mcr-install; \
    mkdir -p /opt/mcr; \
    mkdir -p /execute; \
    mkdir -p /home/developer; \
    (export uid=1000 gid=1000 && \
    mkdir -p /home/developer && \
    echo "developer:x:${uid}:${gid}:Developer,,,:/home/developer:/bin/bash" >> /etc/passwd && \
    echo "developer:x:${uid}:" >> /etc/group && \
    echo "developer ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/developer && \
    chmod 0440 /etc/sudoers.d/developer && \
    chown ${uid}:${gid} -R /home/developer) & \
    (wget http://ssd.mathworks.com/supportfiles/downloads/R2018b/deployment_files/R2018b/installers/glnxa64/MCR_R2018b_glnxa64_installer.zip -P /mcr-install; \
    unzip -q /mcr-install/MCR_R2018b_glnxa64_installer.zip -d /mcr-install; \
    ./mcr-install/install -destinationFolder /opt/mcr -agreeToLicense yes -mode silent; \
    rm -rf mcr-install) & \
    (wget --no-check-certificate https://cloud.biohpc.swmed.edu/index.php/s/C6F5PwEgEe7atTa/download -O download.zip; \
    unzip download.zip; \
    mv for_testing /execute/utrack; \
    chmod +x /execute/utrack/run_utrack.sh /execute/utrack/utrack; \
    rm download.zip) & \
    wait

# Configure environment variables for MCR
ENV LD_LIBRARY_PATH /opt/mcr/v95/runtime/glnxa64:/opt/mcr/v95/bin/glnxa64:/opt/mcr/v95/sys/os/glnxa64:/opt/mcr/v95/extern/bin/glnxa64

# Configure to use the DISPLAY ENV variable for the GUI
ENV DISPLAY :0
