This directory contains the docker images for
[Mango](https://www.github.com/bigdatagenomics/mango-jenkins). This container contains
all requirements for the [Mango](https://github.com/bigdatagenomics/mango) build
for running with Jenkins.

Running
===

When the runtime container is run, the following environment variables should be
specified:

- SPARK_VERSION: Spark Version
- HADOOP_VERSION: Hadoop version
- COVERALLS_REPO_TOKEN: Token for Coveralls
- WORKSPACE: Workspace where the current mango repository is pulled


An example command to run mango Jenkins tests is:

```

docker run -v $WORKSPACE:${WORKSPACE} \
	-e COVERALLS_REPO_TOKEN=${COVERALLS_REPO_TOKEN} \
	-e WORKSPACE=${WORKSPACE} \
	-e SPARK_VERSION=${SPARK_VERSION} \
	-e HADOOP_VERSION=${HADOOP_VERSION} \
	-e SCALAVER=${SCALAVER} \
	--entrypoint=${WORKSPACE}/scripts/jenkins-test \
	bigdatagenomics/mango-jenkins:latest

```
