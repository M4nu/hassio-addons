ARG BUILD_FROM

FROM ${BUILD_FROM}

RUN apt-get update && apt-get -y install --no-install-recommends git cmake build-essential \
    libasound2-dev qtbase5-dev libqt5serialport5-dev libqt5sql5-sqlite libqt5svg5-dev libqt5x11extras5-dev libusb-1.0-0-dev \
    python3-minimal rpm libcec-dev libxcb-image0-dev libxcb-util0-dev libxcb-shm0-dev libglvnd-dev \
    libxcb-render0-dev libxcb-randr0-dev libxrandr-dev libxrender-dev libavahi-core-dev libavahi-compat-libdnssd-dev \
    libjpeg-dev libturbojpeg0-dev libssl-dev zlib1g-dev ca-certificates curl wget dialog apt-utils \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

COPY run.sh /
RUN chmod a+x /run.sh

#ENV VERSION 17.0.0.0
#ENV FILENAME HyperHDR-${VERSION}-Linux-aarch64.deb

#RUN wget https://github.com/awawa-dev/HyperHDR/releases/download/v${VERSION}/${FILENAME} \
#    && apt-get install -y ./${FILENAME} \
#    && rm -f *.deb

COPY HyperHDR-18.0.0.0beta1-Linux-aarch64.deb /
RUN apt-get install -y /HyperHDR-18.0.0.0beta1-Linux-aarch64.deb && rm /HyperHDR-18.0.0.0beta1-Linux-aarch64.deb

COPY lut_lin_tables.3d.tar.gz /

RUN tar -xf lut_lin_tables.3d.tar.gz -C /usr/share/hyperhdr/lut/ \
    && rm /lut_lin_tables.3d.tar.gz 

EXPOSE 8090 8092 19333 19400 19444 19445

CMD [ "/run.sh" ]
