FROM jennyzouutsw/mcr2020a:1.0.0
LABEL author="Jon Gesell"

#Download and install Utrack 3D 1.0
    RUN mkdir -p /execute; \
    wget --no-check-certificate https://cloud.biohpc.swmed.edu/index.php/s/tiK5XKYLbPsDt6J/download -O download.zip; \
    unzip download.zip; \
    mv for_testing /execute/utrack3d; \
    chmod +x /execute/utrack3d/run_utrack3D.sh /execute/utrack3d/utrack3D; \
    rm download.zip