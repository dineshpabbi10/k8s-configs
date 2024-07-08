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
- See postgres-cluster.yaml for reference yaml
- Edit database name, make sure it's unique within cluster
- Run `kubectl apply -f <pg-cluster-config-file-you-created.yaml>`
  
## How to create a backup
- See backup.yaml for reference
- Simply change cluster name in the config file u create to targeta databse

## How to recover from a backup
- See recover-cluster.yaml file for reference
  
## How to view database credentials
- Enter `kubectl get secrets`. Add -n <namespace> option if database was applied to a namespace
- From the list secrets. Locate <db-name>-app secret
- Run `kubectl get secrets <secretname with -app> -o yaml`. Example : `kubectl get secrets cluster-ai-app -n pg-clusters -o yaml`
- Decode password and username using base64 decode manually
  
## How to connect locally
- For the database name you selected , run : `kubectl port-forward service/<dbname>-rw 5432:5432`. If database was created in a namespace, run : `kubectl port-forward service/<db-name>-rw 5432:5432 -n <namespace>`
- Get database credentials from secrets
- Should be able to connect on localhost:5432

## How to connect with app deployed in k8s cluster
https://cloudnative-pg.io/documentation/1.20/applications/#connecting-from-an-application
