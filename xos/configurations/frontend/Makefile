MYIP:=$(shell hostname -i)
RUNNING_CONTAINER=$(shell sudo docker ps|grep "xos"|awk '{print $$NF}')
LAST_CONTAINER=$(shell sudo docker ps -l -q)
XOS_FOLDER=$(shell pwd)

all: frontend

frontend:
	sudo apt-get -y install httpie
	cat ../common/Dockerfile.common Dockerfile.frontend > Dockerfile
	cd ../../..; sudo docker build -t xos -f xos/configurations/frontend/Dockerfile .
	echo $(XOS_FOLDER)
	sudo docker run -v $(XOS_FOLDER)/../../core/xoslib:/opt/xos/core/xoslib -p 9000:8000 --add-host="0.0.0.0:127.0.0.1" xos
	#sudo docker run -d --add-host="0.0.0.0:$(MYIP)" -p 9999:8000 xos
	bash ../common/wait_for_xos.sh
	echo $(RUNNING_CONTAINER)

stop:
	sudo docker stop $(RUNNING_CONTAINER)

start:
	sudo docker start $(LAST_CONTAINER)

showlogs:
	sudo docker logs $(LAST_CONTAINER)

enter:
	sudo docker exec -t -i $(RUNNING_CONTAINER) bash
