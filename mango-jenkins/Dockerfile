FROM bigdatagenomics/miniconda3-maven3-openjdk8

MAINTAINER Alyssa Morrow, akmorrow@berkeley.edu

# Environment Variables
ARG SPARK_VERSION
ARG HADOOP_VERSION
ARG COVERALLS_REPO_TOKEN
ARG WORKSPACE

WORKDIR /home

# Install make and pip/python dependencies
# uuid-runtime: for unique identifiers used in conda envs
RUN apt-get update && apt-get install -y \
  git \
  make \
  python3.5 \
  python3-pip \
  nodejs \
  uuid-runtime \
  python-tk \
  chromium

# set chromium environment variable for mango-pileup karma tests
ENV CHROME_BIN=/usr/bin/chromium

# install node/npm
RUN conda install -y nodejs

ENTRYPOINT ["${WORKSPACE}/scripts/jenkins-test"]
