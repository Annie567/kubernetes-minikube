# Kubernetes Minikube Project

## Author
Annie567

---

## Project Overview

This project demonstrates how to:

- Build a Docker image
- Publish it to Docker Hub
- Deploy it on Kubernetes using Minikube
- Expose it via NodePort and LoadBalancer
- Use YAML configuration files
- Configure Ingress routing
- Scale and update deployments

---

## 1. Docker Installation

For Mac / Windows 10 Pro / Enterprise / Education:
https://www.docker.com/get-started

Choose **Docker Desktop**

For Windows Home:
https://docs.docker.com/docker-for-windows/install-windows-home/

---

## 2. Minikube Installation

https://minikube.sigs.k8s.io/docs/start/

Start Minikube:

minikube start --driver=docker

Open dashboard:

minikube dashboard

---

## 3. Build and Test with Docker

Go to the project directory:

cd kubernetes-minikube/myservice

Build image:

docker build -t myservice .

Check image:

docker images

Run container:

docker run -p 4000:8080 -t myservice

Open in browser:

http://localhost:4000

Stop container:

docker ps
docker stop CONTAINER_ID

---

## 4. Publish Image to Docker Hub

Docker Hub repository:
https://hub.docker.com/r/annieaurora/myservice

Tag image:

docker tag myservice annieaurora/myservice:1

Login:

docker login

Push:

docker push annieaurora/myservice:1

---

## 5. Create Kubernetes Deployment

Create deployment:

kubectl create deployment myservice --image=annieaurora/myservice:1

Check pods:

kubectl get pods
kubectl describe pods

Enter container:

kubectl exec -it POD_NAME -- /bin/bash

---

## 6. Expose Deployment (NodePort)

kubectl expose deployment myservice --type=NodePort --port=8080

Retrieve service URL:

minikube service myservice --url

---

## 7. Scaling

Scale to 2 replicas:

kubectl scale --replicas=2 deployment/myservice

Check status:

kubectl get deployments
kubectl get pods

---

## 8. LoadBalancer Service

Delete previous service:

kubectl delete service myservice

Create LoadBalancer:

kubectl expose deployment myservice --type=LoadBalancer --port=8080

Get URL:

minikube service myservice --url

---

## 9. Rolling Updates

Update image:

kubectl set image deployments/myservice myservice=annieaurora/myservice:1

Check rollout status:

kubectl rollout status deployments/myservice

Rollback:

kubectl rollout undo deployments/myservice

---

## 10. Deploy Using YAML Files

Apply deployment:

kubectl apply -f myservice-deployment.yml

Apply NodePort service:

kubectl apply -f myservice-service.yml

Apply LoadBalancer service:

kubectl apply -f myservice-loadbalancing-service.yml

---

## 11. Ingress Configuration

Enable ingress:

minikube addons enable ingress

Apply ingress configuration:

kubectl apply -f ingress.yml

Check ingress:

kubectl get ingress

Edit hosts file (Mac / Linux):

127.0.0.1 myservice.info

Then open:

http://myservice.info

---

## 12. Delete Resources

kubectl delete service myservice
kubectl delete deployment myservice

---

## Project Links

Docker Image:
https://hub.docker.com/r/annieaurora/myservice

GitHub Repository:
https://github.com/Annie567/kubernetes-minikube
