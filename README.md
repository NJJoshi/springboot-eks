# Steps to Build & Run Application on AWS Elastic Kubernetes Services

### Step 1: Clone and Build Spring Boot application on local
    Clone application using below mentioned command
    git clone https://github.com/NJJoshi/springboot-eks.git
### Step 2: Run docker on your local to push spring boot application on your local Docker 
    Run below mentioned command to build & push spring boot app jar on local running docker instance
    docker build -t springboot-eks .
### Step 3: Make sure your local is connected to AWS Cloud using AWS CLI
    You need to do make sure that your local machine is connected to AWS Cloud using AWS CLI instance.
    If you are not set up with your AWS CLI , Please follow instructions mentioned into below mentioned URL
    https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-files.html
### Step 4: Deploy local docker image to AWS Elastic Container Service (ECS)
    Make sure you will be having one repository created on AWS ECR so that we can push our local running docker image to ECR.
    1. You need to tag your local docker image 
        docker tag springboot-eks:latest <ECR Repository URL>
    2. You need to push that tagged image to ECR 
        docker push <ECR Repository URL>
### Step 5: Deploy AWS ECR Image to AWS EKS
Please follow below mentioned steps to achieve it.
#### Create EKS Cluster

```eksctl create cluster --name jt-cluster --version 1.28 --nodes=1 --node-type=t2.small --region us-east-2```

#### Configure kubectl to Use the EKS Cluster

```aws eks --region us-east-2 update-kubeconfig --name javatechie-cluster```
