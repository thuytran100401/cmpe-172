clean:
	mvn clean

compile:
	mvn compile

run:
	mvn spring-boot:run

build:
	mvn package

run-jar:
	java -jar target/demo-docker-1.0.jar

# Docker

docker-build: jar
	docker build --platform=linux/amd64 -t demo-docker .
	docker images

docker-run: docker-build
	docker run --name demo-docker1 -td -p 81:8080 demo-docker	
	docker ps

docker-clean:
	docker stop spring-hello
	docker rm spring-hello
	docker rmi spring-hello

docker-shell:
	docker exec -it spring-hello bash 

docker-push:
	docker login
	docker build -t $(account)/spring-hello:latest -t $(account)/spring-hello:latest .
	docker push $(account)/spring-hello:latest 


# Pod

pod-run:
	kubectl apply -f pod.yaml

pod-list:
	kubectl get pods

pod-desc:
	kubectl describe pods spring-hello

pod-delete:
	kubectl delete -f pod.yaml

pod-shell:
	kubectl exec -it spring-hello -- /bin/bash

pod-logs:
	kubectl logs -f spring-hello

# Service

service-create:
	kubectl create -f service.yaml

service-get:
	kubectl get services

service-get-ip:
	kubectl get service spring-hello -o wide

service-delete:
	kubectl delete service spring-hello