# Kubernetes-Wordpress
The aim of this project is to create a deployable kubernetes cluster of 2 containers: 
- wordpress instance
- mariadb 

## Deploying to GCP
### project setup
`gcloud config set compute/region us-east1`
`export PROJECT_ID=wls-pro-citecycles`
`git clone https://github.com/WLSPro/kubernetes-wordpress`
`cd kubernetes-wordpress`
`WORKING_DIR=$(pwd)`

### create cluster
`CLUSTER_NAME=wordpress-cluster`
`gcloud container clusters create-auto $CLUSTER_NAME`

### connect to cluster
`gcloud container clusters get-credentials $CLUSTER_NAME --region us-east1`
`kubectl apply -f mariadb-deployment.yaml`
`kubectl apply -f mariadb-service.yaml`
`kubectl apply -f wordpress-deployment.yaml`
`kubectl apply -f wordpress-service.yaml`

### get external IP address
kubectl get svc
