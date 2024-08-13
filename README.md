# Demo Continuous Deployment to Kubernetes
This repository is part of a continuous deployment (CD) setup for deploying a sample Python web application microservice to a Kubernetes cluster. 
The repository is designed to work in conjunction with the [Demo CI repository](https://github.com/sarubhai/demo_ci), which contains the source code and CI (Continuous Integration) pipelines for building and testing the application.

## Overview
The purpose of this repository is to demonstrate continuous deployment to a Kubernetes cluster using two different approaches:

- GitHub Actions with kubectl: Deploying the application directly to the Kubernetes cluster using GitHub Actions.
- Argo CD: Deploying the application by allowing Argo CD to monitor the repository and automatically apply changes to the cluster.

### Kubernetes Manifests
This repository contains Kubernetes manifests for deploying the application, including resources for deployment, service, and ingress.
#### Deployment
The deployment.yaml file defines the deployment configuration for the application, including the number of replicas, container image details, and environment variables.

- Deployment Name: demo-app
- Replicas: 3
- Container: A single container running the Python web application
- Image: sarubhai/demo-app:latest (Replaced with the latest image via continuous integration)
- Ports: Container listens on port 5000

#### Service
The service.yaml file defines the service configuration to expose the application within the Kubernetes cluster, including the service type and port.

- Service Name: demo-app-service
- Type: ClusterIP (internal cluster access)
- Port: Exposes port 5000 internally and targets port 5000 on the pods

#### Ingress
The ingress.yaml file defines the ingress configuration to expose the application externally, including host routing and TLS settings.

- Ingress Name: demo-app-ingress
- Host: Configurable host for routing traffic
- TLS: Optional TLS configuration for securing traffic
