FROM ubuntu:22.04
RUN apt -y update
RUN apt -y dist-upgrade
RUN apt -y install --no-install-recommends git python3-pip
RUN python3 -m pip install --user --no-warn-script-location ansible ansible-core
ENV PATH="${PATH}:/root/.local/bin"
WORKDIR "/repo"
