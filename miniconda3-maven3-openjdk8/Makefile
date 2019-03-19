# Definitions
build_output = ${runtime_path}/miniconda3-maven3-openjdk8
git_commit ?= $(shell git log --pretty=oneline -n 1 | cut -f1 -d " ")
name = bigdatagenomics/miniconda3-maven3-openjdk8
tag = 0.0.1--${git_commit}
build_tool = runtime-container.DONE

# Steps
build: Dockerfile
	cd ../maven3-openjdk8 && make build
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
