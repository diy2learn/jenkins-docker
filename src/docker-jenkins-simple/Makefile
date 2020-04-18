JENKINS_PORT=8080

dcp-up:
	docker-compose up -d

dcp-down:
	docker-compose down

check:
	curl $$MY_DOMAIN:$(JENKINS_PORT)

inspect:
	docker exec jenkins-master ps -ef | grep java
