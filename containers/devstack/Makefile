CONTAINER_NAME:=xos-devstack
IMAGE_NAME:=xosproject/xos-devstack
NO_DOCKER_CACHE?=false

.PHONY: build
build: ; docker build --no-cache=${NO_DOCKER_CACHE} --rm -t ${IMAGE_NAME} .

.PHONY: run
run: ; docker run -d --name ${CONTAINER_NAME} -p 80:8000 ${IMAGE_NAME}

.PHONY: stop
stop: ; docker stop ${CONTAINER_NAME}

.PHONY: rm
rm: ; docker rm ${CONTAINER_NAME}

.PHONY: rmi
rmi: ; docker rmi ${IMAGE_NAME}
