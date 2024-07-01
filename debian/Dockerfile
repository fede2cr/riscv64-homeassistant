FROM docker.io/riscv64/debian:rc-buggy-20240612

RUN useradd -rm -s /bin/bash homeassistant && \
mkdir /srv/homeassistant && \
chown homeassistant:homeassistant /srv/homeassistant

RUN apt-get update && apt-get upgrade -y && \
apt-get install -y --no-install-recommends \
python3 python3-dev python3-venv python3-pip \
bluez \
libffi-dev \
libssl-dev \
libjpeg-dev \
zlib1g-dev \
autoconf \
build-essential \
libopenjp2-7 \
libtiff6 \
libturbojpeg0-dev \
tzdata \
ffmpeg \
liblapack3 \
liblapack-dev \
libatlas-base-dev \
rustup \
cmake \
automake \
libopenblas64-0 libopenblas64-dev \
libavformat61 libavformat-dev \
libavcodec61 libavcodec-dev \
libavdevice61 libavdevice-dev \
libavutil59 libavutil-dev \
libavfilter10 libavfilter-dev \
libswscale8 libswscale-dev \
libswresample5 libswresample-dev \
libpcap-dev \
isal libisal-dev libisal2 \
libopenblas-dev libopenblas0 \
&& apt-get clean && \
rm -rf /var/lib/apt/lists/*


USER homeassistant

RUN rustup default stable

RUN cd /srv/homeassistant && \
python3 -m venv . && \
. bin/activate && \
python3 -m pip install wheel && \
pip3 install homeassistant==2024.6.4 && \
pip install --quiet python-matter-server==6.1.0 --upgrade --constraint /srv/homeassistant/lib/python3.12/site-packages/homeassistant/package_constraints.txt && \
pip install -r /srv/homeassistant/lib/python3.12/site-packages/homeassistant/package_constraints.txt
