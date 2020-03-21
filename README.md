# Photo Sharing Application

This is a simple cloud application developed alongside the Udacity Cloud Engineering Nanodegree. It allows users to register and log into a web client, post photos to the feed, and process photos using an image filtering microservice.

## Architecture
There a four microservices:
1. User API - Manages the authentication of the user.  This is not public facing and is only accesible through the reverseproxy.
2. Feed API - Handles requests related to the posts.  This is not public facing and is only accesible through the reverseproxy.
3. Reverseproxy - This server routes traffic to the Feed API or User API depending on the request.
4. Frontend - This is the UI and is built using the Ionic framework

## Dependencies
This project depends on Nodejs, NPM and the Ionic CLI.
[https://nodejs.com/en/download](https://nodejs.org/en/download/)
[Ionic Framework Docs](https://ionicframework.com/docs/installation/cli)


## Configure The Frontend
The Frontend application uses enviornment files located in `./frontend/src/enviornments/environment.*.ts` to load configuration variables at runtime. By default `environment.ts` is used for development and `environment.prod.ts` is used for production. The `apiHost` variable should be set to your server url either locally or in the cloud.


## Setup Docker Environment

To view all available contexts:
```kubectl config get-contexts```

To change the context:
```kubectl config use-context docker-for-desktop```


# Kubernetes

## Setup on AWS
If you want to use this on AWS, you can use the `eksctl` cli.
[eksctl CLI](https://docs.aws.amazon.com/eks/latest/userguide/getting-started-eksctl.html)

```eksctl create cluster --name=<CLUSTER_NAME> --region=<REGION_NAME> --fargate```

You can switch between the AWS and your local environment by managinf contexts.  To view the available contexts:

```kubectl config get-contexts```

To change the context:

```kubectl config use-context <CONTEXT_NAME>```


### Setup up the configmaps and secrets:
The `deployment/k8s` folder contains the Kubernetes manifests to deploy the application.  

```kubectl create secret generic env-secret --from-literal=POSTGRESS_USERNAME=<> --from-literal=POSTGRESS_PASSWORD=<>```
```kubectl create secret generic aws-secret --from-file=<PATH_TO_AWS_CREDENTIALS>```

The `examples` folder contains the template for env-config configmap.

```kubectl create -f env-configmap.yaml```

### Setup

```kubectl create -f backend-feed-deployment.yaml```
```kubectl create -f backend-feed-service.yaml```

```kubectl create -f backend-user-deployment.yaml```
```kubectl create -f backend-user-service.yaml```

```kubectl create -f reverseproxy-deployment.yaml```
```kubectl create -f reverseproxy-service.yaml```

```kubectl create -f frontend-deployment.yaml```
```kubectl create -f frontend-service.yaml```

