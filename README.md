# Kubernetes Minikube Project

## Author
Annie567

## Docker Image
Docker Hub image:
https://hub.docker.com/r/annieaurora/myservice

Image name:
annieaurora/myservice:1

## Build Docker Image

docker build -t myservice .
docker tag myservice annieaurora/myservice:1
docker push annieaurora/myservice:1

## Kubernetes Deployment

Start minikube:

minikube start --driver=docker

Create deployment:

kubectl create deployment myservice --image=annieaurora/myservice:1

Expose service:

kubectl expose deployment myservice --type=NodePort --port=8080

Check:

kubectl get pods
kubectl get svc

Access service:

kubectl port-forward svc/myservice 4000:8080

Open browser:
http://localhost:4000

## YAML Files

Apply yaml files:

kubectl apply -f myservice-deployment.yml
kubectl apply -f myservice-service.yml
