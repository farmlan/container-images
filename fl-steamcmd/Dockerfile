FROM ubuntu:24.04

ARG PUID=1000
ARG PGID=1000
ARG USER=farmlan
ARG HOMEDIR=/home/${USER}
ARG STEAMCMDDIR=${HOMEDIR}/steamcmd

RUN useradd --create-home --user-group ${USER}

RUN echo steam steam/license note '' | debconf-set-selections \ 
    && echo steam steam/question select "I AGREE" | debconf-set-selections \
    && dpkg --add-architecture i386 \
    && apt update \
    && apt upgrade -y \
    && apt -y install steamcmd \
    && apt -y install curl \
    && ln /usr/games/steamcmd /usr/bin/steamcmd

USER ${USER}

WORKDIR ${HOMEDIR}