FROM jennyzouutsw/mcr2020a:1.0.0
LABEL author="Jon Gesell"

#Install Utrack 2.3
RUN wget --no-check-certificate https://cloud.biohpc.swmed.edu/index.php/s/3DswCQyjf35G3YC/download -O download.zip; \
    unzip download.zip; \
    mv for_testing /execute/utrack; \
    chmod +x /execute/utrack/run_utrack.sh /execute/utrack/utrack; \
    rm download.zip;