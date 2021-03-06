FROM    debian:bullseye-slim

LABEL   author="Torsten Widmann" maintainer="info@goover.de"

ENV     DEBIAN_FRONTEND noninteractive

RUN         dpkg --add-architecture i386 \
            && apt update \
            && apt upgrade -y \
            && apt install -y tar curl gcc g++ lib32gcc-s1 libgcc1 libcurl4-gnutls-dev:i386 libssl1.1:i386 libcurl4:i386 lib32tinfo6 libtinfo6:i386 lib32z1 lib32stdc++6 libncurses5:i386 libcurl3-gnutls:i386 libsdl2-2.0-0:i386 iproute2 gdb libsdl1.2debian libfontconfig1 telnet net-tools netcat tzdata \
            && apt install -y libstdc++6 libstdc++6:i386 libc6-amd64 libc6:i386 psmisc libgdiplus libcurl4 libfontconfig1 libpangocairo-1.0-0 libnss3 libgconf-2-4 libxi6 libxcursor1 libxss1 libxcomposite1 libasound2 libxdamage1 libxtst6 libatk1.0-0 libxrandr2 libcurl4 xvfb mesa-utils git \
            && apt install -y python3 python3-dev python3-pip

RUN     apt update -y \
          && apt upgrade -y \
          && apt install -y apt-transport-https wget iproute2 sqlite3 \
          && wget https://packages.microsoft.com/config/debian/11/packages-microsoft-prod.deb -O packages-microsoft-prod.deb \
          && dpkg -i packages-microsoft-prod.deb \
          && rm packages-microsoft-prod.deb \
          && apt update -y \
          && apt install -y aspnetcore-runtime-6.0 libgdiplus

RUN     useradd -d /home/container -m container

USER    container
ENV     USER=container HOME=/home/container
WORKDIR /home/container

COPY    ./../entrypoint.sh /entrypoint.sh
CMD     ["/bin/bash", "/entrypoint.sh"]
