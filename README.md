# Kubernetes-EKS-
# AWS EKS Cluster Setup using eksctl

## Overview
This project explains how to setup a Kubernetes cluster in AWS using Amazon EKS and eksctl.

EKS (Elastic Kubernetes Service) is a managed Kubernetes service provided by AWS.

Using this setup we can:
- Create Kubernetes Cluster
- Manage Worker Nodes
- Deploy Applications
- Practice Kubernetes Commands

---

# Prerequisites

- AWS Account
- EC2 Instance (Ubuntu)
- IAM Permissions
- Internet Connection

---

# Architecture

Developer
   ↓
EC2 Management Host
   ↓
kubectl / eksctl
   ↓
AWS EKS Cluster
   ↓
Worker Nodes
   ↓
Pods & Containers

---

# Step - 1 : Create EC2 Management Host

## Launch Ubuntu EC2 Instance

Recommended:
- OS : Ubuntu
- Instance Type : t2.micro

Connect to machine using SSH.

---

# Step - 2 : Install kubectl

kubectl is Kubernetes command line tool used to communicate with cluster.

Run below commands:

```bash
curl -o kubectl https://amazon-eks.s3.us-west-2.amazonaws.com/1.19.6/2021-01-05/bin/linux/amd64/kubectl

chmod +x ./kubectl

sudo mv ./kubectl /usr/local/bin

kubectl version --short --client

kubectl version --client



AWS CLI is used to interact with AWS services.

Run below commands:

sudo apt update

sudo apt install unzip -y

curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"

unzip awscliv2.zip

sudo ./aws/install

aws --version

Step - 4 : Install eksctl

eksctl is a CLI tool used to create and manage EKS clusters.

Run below commands:

curl --silent --location \
"https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" \
| tar xz -C /tmp

sudo mv /tmp/eksctl /usr/local/bin

eksctl version

Verify:

eksctl version
Step - 5 : Create IAM Role
Create Role
Open AWS IAM Service
Click Create Role
Select Use Case : EC2
Add Permission

Attach:

AdministratorAccess
Role Name

Example:

eksroleec2
Step - 6 : Attach IAM Role to EC2

Go to:

EC2
 → Select Instance
 → Security
 → Modify IAM Role
 → Attach IAM Role

Attach:

eksroleec2
Step - 7 : Create EKS Cluster
Syntax
eksctl create cluster \
--name cluster-name \
--region region-name \
--node-type instance-type \
--nodes-min 2 \
--nodes-max 2 \
--zones <AZ-1>,<AZ-2>
Create Cluster in Mumbai Region
eksctl create cluster \
--name ashokit-cluster4 \
--region ap-south-1 \
--node-type t2.medium \
--zones ap-south-1a,ap-south-1b
Create Cluster in N. Virginia Region
eksctl create cluster \
--name ashokit-cluster4 \
--region us-east-1 \
--node-type t2.medium \
--zones us-east-1a,us-east-1b
Cluster Creation Time

Cluster creation may take:

5 to 10 minutes

AWS automatically creates:

Control Plane
Worker Nodes
VPC
Security Groups
Networking Resources
Verify Cluster

Check cluster nodes using below command:

kubectl get nodes

Expected Output:

NAME              STATUS   ROLES    AGE   VERSION
ip-xxx-xxx        Ready    <none>   xxm   v1.xx
Useful Kubernetes Commands
Get Nodes
kubectl get nodes
Get Pods
kubectl get pods
Get Services
kubectl get svc
Get Deployments
kubectl get deployments
Delete EKS Cluster

Important:
Delete cluster after practice to avoid AWS billing charges.

eksctl delete cluster \
--name ashokit-cluster4 \
--region ap-south-1
Advantages of EKS
Managed Kubernetes Service
High Availability
Easy Scaling
Secure Infrastructure
AWS Integration
Production Ready
Technologies Used
Kubernetes
AWS EKS
EC2
IAM
kubectl
eksctl
AWS CLI
Conclusion

Using AWS EKS and eksctl we can quickly create and manage Kubernetes clusters in AWS Cloud. EKS reduces operational overhead by managing Kubernetes control plane automatically.
