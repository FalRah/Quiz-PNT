# Quiz PNT

This repository contains the Kubernetes YAML files to deploy a simple application with a frontend and backend service on an Azure Kubernetes Service (AKS) cluster.

**Frontend:** NGINX

**Backend:** Node.js 

az login
az group create --name pnt-quiz-rg --location eastus
az aks create --resource-group pnt-quiz-rg --name pnt-quiz-cluster --node-count 1 --enable-addons monitoring --generate-ssh-keys
az aks get-credentials --resource-group pnt-quiz-rg --name pnt-quiz-cluster
kubectl create namespace pnt-quiz
kubectl apply -f frontend-deployment.yaml
kubectl apply -f backend-deployment.yaml
kubectl get deployments -n pnt-quiz
kubectl get pods -n pnt-quiz
kubectl get svc -n pnt-quiz
kubectl port-forward svc/nginx-service 8080:80 -n pnt-quiz


Files
frontend-deployment.yaml: Defines the deployment and service for the frontend.
backend-deployment.yaml: Defines the deployment and service for the backend.
