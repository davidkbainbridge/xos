CONTAINER_NAME:=xos-server
TOSCA_CONFIG_PATH:=/opt/xos/configurations/opencloud/opencloud.yaml

.PHONY: build
build: ; docker build --rm -t xos . && ./initdb

.PHONY: run
run: ; docker run -d --name ${CONTAINER_NAME} -p 80:8000 xos

.PHONY: runtosca
runtosca: ; docker exec -it ${CONTAINER_NAME} /usr/bin/python /opt/xos/tosca/run.py padmin@vicci.org ${TOSCA_CONFIG_PATH}

.PHONY: stop
stop: ; docker stop ${CONTAINER_NAME}

.PHONY: rm
rm: ; docker rm ${CONTAINER_NAME}
