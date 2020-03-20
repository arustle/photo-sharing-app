# Udagram Image Filtering Microservice

Udagram is a simple cloud application developed alongside the Udacity Cloud Engineering Nanodegree. It allows users to register and log into a web client, post photos to the feed, and process photos using an image filtering microservice.



## Tasks

### Setup Docker Environment

To view all available contexts:
```kubectl config get-contexts```

To change the context:
```kubectl config use-context docker-for-desktop```



### Setup on AWS

```eksctl create cluster --name=<CLUSTER_NAME> --region=<REGION_NAME> --fargate```
eksctl create cluster --name='photo-sharing-app-cluster' --region='us-east-1 --fargate

To view all available contexts:
```kubectl config get-contexts```

To change the context:
```kubectl config use-context docker-for-desktop```


```kubectl create secret generic env-secret --from-literal=POSTGRESS_USERNAME=<> --from-literal=POSTGRESS_PASSWORD=<>```
```kubectl create secret generic aws-secret --from-file=<>```
```kubectl create -f env-configmap.yaml```

```kubectl create -f backend-feed-deployment.yaml```
```kubectl create -f backend-user-deployment.yaml```
```kubectl create -f reverseproxy-deployment.yaml```
```kubectl create -f frontend-deployment.yaml```

```kubectl create -f backend-feed-service.yaml```
```kubectl create -f backend-user-service.yaml```
```kubectl create -f reverseproxy-service.yaml```
