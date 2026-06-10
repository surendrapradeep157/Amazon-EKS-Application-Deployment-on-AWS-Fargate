Amazon EKS Deployment using AWS Fargate and ALB Ingress
Project Overview

This project demonstrates the deployment of a containerized web application on Amazon EKS using AWS Fargate. The application is exposed to the internet through an AWS Application Load Balancer managed by the AWS Load Balancer Controller.

The objective of this project was to gain hands-on experience with Kubernetes, Amazon EKS, AWS Fargate, IAM, networking, and ingress-based traffic routing.


**AWS Resources Used** : 
    Networking |
Amazon VPC | 
Public Subnets | 
Private Subnets | 
Route Tables | 
Internet Gateway | 
Security Groups |

**Compute** : 
Amazon EKS Cluster | 
AWS Fargate Profile 

**Identity and Access Management** : 
IAM Roles | 
IAM Policies | 
IAM Service Account (IRSA)

**Load Balancing** : 
Application Load Balancer (ALB) |
Target Groups | 
Listener Rules 


**Kubernetes Resources Used** : 
Namespace | 
Deployment | 
Pods | 
Service |
Ingress |
Service Account 

**Tools and Technologies** : 
AWS | 
Amazon EKS |
AWS Fargate |
Kubernetes |
kubectl |
eksctl |
AWS CLI |
Helm | 
Docker 

**Implementation Steps**
**Step 1**: Create EKS Cluster
eksctl create cluster \
  --name demo-cluster \
  --region us-east-1 \
  --fargate

Created the EKS control plane and networking resources.

**Step 2**: Create Fargate Profile
eksctl create fargateprofile \
  --cluster demo-cluster \
  --region us-east-1 \
  --name alb-sample-app \
  --namespace game-2048

Configured AWS Fargate to run workloads deployed in the game-2048 namespace.

**Step 3**: Install AWS Load Balancer Controller

Configured:

IAM Policy
IAM Role
Service Account
Helm Chart

This controller automatically provisions Application Load Balancers based on Kubernetes Ingress resources.

**Step 4**: Deploy Application
kubectl apply -f 2048_full.yaml

Created:

Deployment
Service
Ingress

**Step 5**: Access Application
The AWS Load Balancer Controller automatically:
Created an Application Load Balancer
Registered pod targets
Configured listener rules
Routed external traffic to Kubernetes services

Users could access the application using the ALB DNS endpoint.

**Outcome**

Successfully deployed and exposed a containerized web application on Amazon EKS using AWS Fargate and AWS Application Load Balancer, demonstrating practical knowledge of Kubernetes orchestration and AWS cloud-native services.
