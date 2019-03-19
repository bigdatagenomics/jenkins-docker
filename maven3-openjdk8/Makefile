# Definitions
git_commit ?= $(shell git log --pretty=oneline -n 1 | cut -f1 -d " ")
name = bigdatagenomics/maven3-openjdk8
build_tool = runtime-container.DONE
tag = 0.0.1--${git_commit}

# Steps
build: Dockerfile
	docker build -t ${name}:${tag} .
	-docker rmi ${name}:latest
	docker tag ${name}:${tag} ${name}:latest
	touch ${build_tool}

clean:
	docker rmi -f ${name}:${tag} ${name}:${tag}

push: build
	# Requires ~/.dockercfg
	docker push ${name}:${tag}
	docker push ${name}:latest
