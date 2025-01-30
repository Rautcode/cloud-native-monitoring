# Cloud Native Monitoring Application

This project is a cloud-native monitoring application built with Kubernetes and Docker. It helps in monitoring cloud-based applications and services in a containerized environment. The application is deployed using Kubernetes and Docker, and its deployment is managed through EKS (Elastic Kubernetes Service).

## Features
- Deploys a Flask-based monitoring application.
- Exposes the application via a Kubernetes Service.
- Uses Docker containers for app packaging.
- Can be deployed in any cloud-native environment (AWS, GCP, Azure, etc.)

## Prerequisites
Before setting up the project, ensure you have the following installed:

- Docker
- Kubernetes (kubectl)
- AWS CLI (for EKS and related resources)
- Python
- Git

## Setup Instructions

### 1. Clone the Repository

Clone the repository to your local machine:
```sh
git clone https://github.com/your-username/cloud-native-monitoring.git
```

### 2. Build the Docker Image

Navigate to the project directory and build the Docker image:

docker build -t my_monitoring_app_image .

### 3. Push the Docker Image to Amazon ECR

Authenticate with Amazon ECR and push the image:

aws ecr get-login-password --region ap-south-1 | docker login --username AWS --password-stdin 982534379850.dkr.ecr.ap-south-1.amazonaws.com
docker tag my_monitoring_app_image:latest 982534379850.dkr.ecr.ap-south-1.amazonaws.com/my_monitoring_app_image:latest
docker push 982534379850.dkr.ecr.ap-south-1.amazonaws.com/my_monitoring_app_image:latest


### 4. Set Up Kubernetes Cluster

Create an EKS cluster (skip if already set up) and ensure your kubectl is configured to connect to the cluster:

aws eks --region ap-south-1 update-kubeconfig --name my-cluster


### 5. Deploy the Application

Apply the Kubernetes deployment and service files:

kubectl apply -f deployment.yaml
kubectl apply -f service.yaml

### 6. Expose the Service

Expose the service locally or use a LoadBalancer:

kubectl port-forward svc/my-flask-service 5000:5000

### 7. Access the Application

Once the service is up, open a browser and go to:
http://localhost:5000

## Screenshots

1. Running Application:
   ![image](https://github.com/user-attachments/assets/17ccf59e-30c9-40aa-a030-2cd362abf29b)

2. Kubernetes Dashboard:
   This project demonstrates a cloud-native monitoring application deployed on **AWS EKS**.
   ![image](https://github.com/user-attachments/assets/f47f41ed-802f-49b2-8e88-38b19247c3f3)

