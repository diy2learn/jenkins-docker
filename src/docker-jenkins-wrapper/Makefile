IMAGE='jenkins/jenkins'

d-build:
	docker build -t myjenkins .
d-run:
	docker run -p 8080:8080 --name=jenkins-master -d myjenkins
d-run-volume:
	docker run -p 8080:8080 -p 50000:50000 --name=jenkins-master \
	 --mount source=jenkins-log,target=/var/log/jenkins \
	--mount source=jenkins-data,target=/var/jenkins_home -d myjenkins

d-stop:
	 docker stop jenkins-master

d-rm: d-stop
	docker rm jenkins-master

d-log:
	docker exec jenkins-master tail -f /var/log/jenkins/jenkins.log
d-cp-log:
	docker cp jenkins-master:/var/log/jenkins/jenkins.log

d-volumes:
	docker volume create jenkins-data
	docker volume create jenkins-log

d-ls-volumes:
	docker volume ls| grep jenkins

version:
	docker inspect $(IMAGE) |grep -i version

dcp-up:
	docker-compose up -d

dcp-down:
	docker-compose down
inspect:
	docker exec jenkins-master ps -ef |grep java 
inspect_env:
	docker-compose run jenkins env|grep -i java

