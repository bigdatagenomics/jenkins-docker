FROM bigdatagenomics/miniconda3-maven3-openjdk8

MAINTAINER Alyssa Morrow, akmorrow@berkeley.edu

# Environment Variables
ARG SPARK_VERSION
ARG HADOOP_VERSION
ARG COVERALLS_REPO_TOKEN
ARG WORKSPACE

WORKDIR /home

# add group and user for jenkins
RUN groupadd jenkins
RUN useradd -ms /bin/bash jenkins -g jenkins

# Install make and pip/python dependencies
# gcc: required for psutil used in python setup.py scripts
# uuid-runtime: for unique identifiers used in conda envs
# libappindicator3-1: missing library required for chrome
RUN apt-get update && apt-get install -y \
  git \
  make \
  gcc \
  uuid-runtime \
  libappindicator3-1

#  python3.5 \
#  python3-pip \
#  nodejs \
#  python-tk \

# install chrome
RUN wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
RUN dpkg -i google-chrome-stable_current_amd64.deb; apt-get -fy install

# set chromium environment variable for mango-pileup karma tests
ENV CHROME_BIN=/usr/bin/google-chrome-stable

# install node/npm
RUN conda install -y nodejs

ENTRYPOINT ["${WORKSPACE}/scripts/jenkins-test"]
