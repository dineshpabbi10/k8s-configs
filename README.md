# Postgres Clusters with Kubernetes

## Pre-Requisites
- CloundativePG K8s operator
- K8s cluster containing AWS secrets 
```
kubectl create secret generic aws-creds \
  --from-literal=ACCESS_KEY_ID=<access key here> \
  --from-literal=ACCESS_SECRET_KEY=<secret key here>
```
- Set kubeconfig env variable to path of kubeconfig file (attached in 1 password)

## How to create a database cluster

## How to view database credentials

## How to connect locally

## How to connect with app deployed in k8s cluster
