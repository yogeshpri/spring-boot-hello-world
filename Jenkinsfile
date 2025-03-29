#!/bin/bash

mvn clean install

docker build -t yogeshpri/my_spring_app:latest .

if docker ps -a | grep 'yogeshpri/my_spring_app'; then
  docker stop yogeshpri/my_spring_app
  docker rm -f yogeshpri/my_spring_app
fi

docker run -d -p 8888:8080 --name yogeshpri/my_spring_app yogeshpri/my_spring_app

mvn test

docker login -u yogeshpri -p "Docker PAT"

docker commit java-spring yogeshpri/java-spring:latest

docker push yogeshpri/java-spring:latest

kubectl delete deploy,svc --all

kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
